

1.进入要管理的目录
2.git init  初始化，即：让git帮助我们管理当前文件夹
3.git status  检测当前目录下文件的状态
4.三种状态的变化
	。红色： 新增文件夹/修改了原老文件  ->git add  文件名
	。绿色： git已经管理起来  -> git commit -m '描述信息'
	。生成版本



想要让git对一个目录进行版本控制需要以下步骤：（工作区，暂存区，版本库）
1.进入要管理的目录
2.执行初始化命令
	git init
3.管理目录下的文件状态
	git status
	注：新增的文件和修改过的文件都是红色
4.管理指定文件（红变绿）
	git add  文件名  （单独文件）
	git add  .    （全部文件）
5.个人信息配置 ： 用户名 邮箱
	git config --global user.email '邮箱'
	git config --global user.name '姓名'
6.生成版本
	git commit -m '描述信息'
7.查看版本命令
	git log
8.回滚至之前版本
	git log 查看全部版本
	git reset --hard 版本号
9.回滚至之后版本
	git reflog 
	git reset --hard 版本号

命令总结
1.查看分支
	git branch
2.创建分支
	git branch  分支名称
3.切换分支
	git checkout 分支名称
4.分支合并 （可能产生冲突）
	git merge 要合并的分支
	注意：切换分支在合并
5.删除分支 
	git branch -d 分支名称

（在家开发）
1.给远程仓库起别名
	git remote add origin  远程仓库地址
2.向远程推送代码
	git push -u origin 分支
（第一次在公司开发）
3.克隆远程仓库代码
	git clone 远程仓库地址（内部已实现git  remote add origin  远程仓库地址）
4.切换分支
	git checkout  分支
（在公司进行开发）
1.切换到dev分支进行开发
	git checkout dev
2.把master分支合并到dev（仅一次）
	git merge master
3.修改代码

4.提交代码
	git add . 
	git commit -m '名称'
	git push origin dev
（回家继续代码）
1.切换到dev分支进行开发
	git checkout dev
2.拉代码
	git pull origin dev
3.继续开发

4.提交代码
	git add . 
	git commit -m '名称'
	git push origin dev
（开发完毕，上线）
1.将dev分支合并到master，进行上线
	git checkout master
	git merge dev
	git push origin master
2.把dev分支也推送到远程
	git checkout dev
	git merge master
	git push origin dev

（快速解决冲突）
1.安装beyond compare
2.在git中配置
	git config --local merge.tool bc3
	git config --local mergetool.path '/url/local/bin/bocmp'
	git config --local mergetool.keepBackup false
3.应用beyond compare解决冲突
	git mergetool



（总结）
1.添加远程链接（别名）
	git remote add origin 地址
2.推送代码
	git push origin dev
3.下载代码
	git clone 地址
4.拉取代码
	git pull origin dev
	等价于
	git fetch origin dev
	git merge origin/dev
5.保持代码提交整洁（变基）
	git rebase 分支
6.记录图形展示
	git log --graph --pretty=format:"%h %s"










进入页面编辑
	vim 要编辑的地址
在页面中更改 
	i
更改完后退出
	esc
返回编辑前
	:q!（退出不保存）
	:wq!（退出并保存）







（其他）
1.项目配置文件：项目/.git/config
	git config --local user.name '姓名'
	git config --local user.email '邮箱'
2.全局配置文件：项目~/.gitconfig
	git config --global user.name '姓名'
	git config --global user.email '邮箱'
3.系统配置文件：项目/etc/.gitconfig
	git config --system user.name '姓名'
	git config --system user.email '邮箱'
	（注：需要root权限）
（应用场景）
	git config --local user.name '姓名'
	git config --local user.email '邮箱'


	git config --local merge.tool bc3
	git config --local mergetool.path '/url/local/bin/bocmp'
	git config --local mergetool.keepBackup false

	gitremote add origin 地址 默认添加在本地配置文件中（--local）


（免密登录）
1.URL中体现
	原来的地址：https://github.com/zph0915/supermall.git
	修改的地址：https://用户名:密码@github.com/zph0915/supermall.git
	
	git remote add origin https://用户名:密码@github.com/zph0915/supermall.git
	git push origin master
2.SSH实现
	1.生成公钥和私钥（默认放在 ~/.ssh目录下，id_rsa.pub公钥 、id_rsa私钥）
		ssh-keygrn
	2.拷贝公钥内容，并设置到github中
	3.在git本地中配置ssh地址
		git remote add origin git@github.com:zph0915/supermall.git
	4.以后使用
		git push origin master
3.git 自动管理凭证


（git忽略文件）
让git 不在管理当前目录下的某些文件
	*.h
	!a.h
	files/
	*.py[c|a|d]
（更多参考：http://github.com/github/gitignore）


（任务管理）
	1.  issues  文档及任务管理
	2.  wiki  项目文档说明