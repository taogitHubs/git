## Git是什么?

​	Git是目前世界上最先进的分布式版本控制系统（没有之一）。Git有什么特点？简单来说就是：高端大气上

## 集中式与分布式

> 集中式版本控制系统:

​    代表: CVS  SVN

​    特点: 版本库集中存放在中央服务器 必须联网才能工作  如果中央服务器的代码被恶意修改了,所有人的代码都	可能会有问题

​	只能跟踪文本文件的改动，比如txt文件，网页，所有的程序代码等

> 分布式版本控制系统:

代表: Git

​    特点: 版本库在自己的电脑上 不需要联网也能工作  安全性高 只能跟踪文本文件的改动，比如txt文件，网页，所有的程序代码等

​          强烈建议使用UTF-8编码 所有语言使用同一种编码，既没有冲突，又被所有平台所支持

## 安装Git

  > 在Linux上安装Git

    1. 如果碰到Ubuntu或Debian 请使用下面命令:

       $ git  //这条命令检查系统中是否有Git

       sudo apt-get install git  // 如果没有,则使用这条命令来进行安装Git

    2. 如果碰到的是 CentOS 请使用下面命令:

      $ git  // 这条命令检查系统中是否有Git

      sudo yum install git
  > 在Windows上安装Git

    1. 如果是32位系统 请使用安装包

       [32位系统的Git](./Other/Git-2.14.3-32-bit.exe)  

    2. 如果是64位系统 请使用安装包

       [64位系统的Git](./Other/Git-2.14.3-64-bit.exe)  
  > 在Mac OS 上安装Git

    自己上Git官网搜索

## 创建版本库

```
第一步： 选择一个所有路径不包含中文的文件夹
第二步： 通过 git init 命令把这个目录变成Git可以管理的仓库
注意： 只要含有.git的目录就是Git仓库（repository）
```

## 工作区&暂存区

```
工作区： 含有.git隐藏文件夹的文件夹 可以被Git管理起来
版本库：就是.git隐藏文件夹 
暂存区：在.git隐藏文件夹中的一个东西-- stage（或者叫index） 作用是暂存所有有修改的文件
        master分支：该分支是Git为我们自动创建的， master分支称之为主分支
        HEAD：指向master的一个指针
        
 查看工作区文件的状态 git status 
```

## 版本回退

```
      第一步： 使用 git log命令查看历史纪录  或者使用 git log --pretty=oneline 让历史记录显示一行
               看到的类似d3fac24271943bfba298765e32b9b0088fdef7b1 是commit id
    
      第二步： 使用git reset --hard HEAD^ 回退到以当前版本为参考点的上一个版本  如果回退100步 就写git reset --hard HEAD~100

      第三步(知道id)： 如果退回去之后又想回来 可以使用 git reset --hard id      id的名字写前几位就好了（一般前七位）

      第四步(不知道id)： 使用 git reflog 来查看每次自己的命令
```

## 管理修改

```
第一步： 新建一个modify.txt文件 添加内容

      第二步： 使用 git add 命令添加文件     把修改放入暂存区

      第三步： 使用git commit 命令提交文件  把暂存区的文件提交到仓库 这时候暂存区被清空
      
      第四步： 修改modify.txt修改内容       

      第五步： 使用git commit 命令提交文件  直接提交，这时候暂存区是干净的， 所以第四步的内容没有被提交上去

      注意： git commit 只会把暂存区的修改提交

```

## 撤销修改

```
现在在你没有使用git add之前有两种选择：
      1. 手动删除你刚才写的那句话
      2. git checkout -- file 可以丢弃工作区的修改

另外就是你使用了git add
      第一步： 使用git reset HEAD file 把已经放到暂存区的文件回退到工作区
      第二步： 再用git checkout -- file 来丢弃工作区的修改
```

## 删除文件

```
通过git 和 commit 操作的文件 如果在文件夹中 自己手动删除 Git是能跟踪到的
      使用 git status
    
    现在你可能遇到了两种情况
      1. 你确实想删除， 那么就用 git rm 命令 将文件从版本库中删除
      2. 你删除错了， 在git commit之前  那么就用 git checkout -- file 撤销
      3. 你删除错了 ，在git commit之后  那么就用git reset --hard id 就可以回退到这个版本下
```

## 创建分支&合并分支

```
第一步：branch dev 创建一个名字为dev的分支
第二步： git checkout dev 切换到dev这个分支
第三步： git branch  列出所有分支
第四步： git branch -d dev 删除dev分支
第五步： git merge 分支的名字 合并分支
```

##解决冲突

```
 出现冲突：
        1.在主分支上有一个文件  conflict.txt 
        2.然后新建一个新分支wanlum
        3.切换到新分支
        4.也新建一个文件 conflict.txt
        5.更改文件的内容 在分支上提交
        6.切换分支到主分支，修改conflict.txt的内容
        7.提交
        8.合并分支
        就出现了冲突

        解决冲突：
          删除找到冲突的地方，手动解决
          解决完后添加并提交

        查看分支合并情况： git log --graph --pretty=oneline --abbrev-commit
    
```

## 分支管理策略

```

```

## bug分支

```
    第一步： 保存当前工作现场，等以后继续工作
              git stash
    第二步： 把分支切换到其他分支 解决完 删除该分支

    第三步： 使用 git stash list 查看存储的工作现场

    第四步： 使用git stash pop来恢复
```





