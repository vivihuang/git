#git相关命令

##创建git版本库
### 1. 初始化  git init

* 用于对本地仓库进行初始化

	    $git init

* 通过ls -ah命令可以查看隐藏的.git文件

		$ls -ah
    
###2. 添加文件  git add 

* 将目录添加到版本库，放至暂存区
    
    	$git add
    
* 添加所有文件

		$git add --all
    
###3. 提交文件  git commit -m ""

* 将文件从本地目录提交到本地仓库

		$git commit -m "hello world"
	
###4. 查看提交记录  git log
* 查看本地版本库提交记录

		$git log
		
###5. 查看git状态  git status

* 查看本地目录文件的git状态

		$git status

##修改本地版本库

###1. 查看修改情况  git diff

* 查看本地文件和本地最新版本库的区别

		$git diff HEAD -- file.name
		$git diff HEAD -- readme.txt

	**注意：只能查看未git add的文件**

###2. 回退版本  git reset 

* 将本地目录退回commit_id版本

		$git log //查看commit_id
		$git reset --hard commit_id

* 将本地目录回退至上一次commit之后的版本

		$git reset --hard HEAD^

* 显示所有提交及回退记录（包括已回退记录），可用于回退旧版本之后再次回到新版本

		$git reflog

###3. 撤销修改

* 撤销修改，让文件回到最近一次git commit或git add时的状态

		$git checkout -- file.name


	若未git add，则退回到最新版本库，即最近的git commit版本

	若已git add，但未git commit，则退回到git add时的版本

###4. 删除文件  git rm file.name
* 从版本库中删除文件

		$git rm file.name

* 若误删本地目录中的文件可用`git checkout -- file.name`从本地版本库中找回

		$git checkout -- file.name

##远程仓库管理
###1. 创建远程库
* 创建SSH Key

    	$ ssh-keygen -t rsa -C "vivihuang126@gmail"
    
	之后一直回车，选择默认值，无需设置密码

	可以在用户主目录`/usr`里找到隐藏的`.ssh`目录，里面有`id_rsa`和`id_rsa.pub`两个文件，这两个就是SSH Key的秘钥对，`id_rsa`是私钥，不能泄露出去，`id_rsa.pub`是公钥。

* 登录git

	登陆`GitHub`，打开`Account settings`，`SSH Keys`页面:
	[Account settings/ SSH Keys](https://github.com/settings/ssh)
	
	选择`Add SSH Keys`，在`Key`文本框里粘贴`id_rsa.pub`文件的内容，之后点击`Add Key`，完成。

* 创建new repo

	登陆`GitHub`，然后，在右上角找到`Create a new repo`按钮，创建一个新的仓库，填入`Repository name`后选择`Create repository`
	
* 在本地目录下创建该repo

		$ git remote add origin https://github.com/vivihuang/repo_name.git
		
* 将本地内容推送至远程库

		$ git push -u origin master
		
###2. 克隆远程库

* 从远程库克隆至本地目录

		$ git clone https://github.com/vivihuang/repo_name.git
		
##分支管理

###1. 创建与合并分支

* 创建并切换至`dev`分支

		$ git branck dev     //创建dev分支
		$ git checkout dev   //切换至dev分支
		Switched to a new branch 'dev'
		
	也可直接用
	
		$ git checkout -b dev
		Switched to a new branch 'dev'
		
* 查看当前分支

		$ git branch
		* dev
  		  master
  		  
 	`git branch`命令会列出所有分支，当前分支前面会标一个*号。
 	
 	此时提交则会在`dev`分支上进行提交。
 		
 * 合并分支
 
 	提交之后可再用`git checkout master`切换回`master`分支
 	
 		$ git checkout master
 		Switched to branch 'master'
 
 	把`dev`分支的工作成果合并到`master`分支上
 	
 		$git merge dev
 		
 	`git merge`命令用于合并指定分支到当前分支，因此必须在切换分支后使用。
 	
 * 删除分支
 
 	合并完成后，就可以放心地删除dev分支了：

		$ git branch -d dev
		Deleted branch dev (was fec145a).

	删除后，查看branch，就只剩下master分支了：

		$ git branch
		* master
		
###2. 解决冲突


 			
	

		
		


	
	
    
