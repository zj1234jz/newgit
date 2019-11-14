1: git 是分布式管理工具，基本是每个人都是一个完整的仓库  和svn集中式不同的是 git甚至无需联网

2：git 下载完毕之后需要配置 
    git config --global user.name ""
    git config --global user.email ""

# 如果你想管理一个目录，那么直接进入到该目录 执行命令 git init 

    初始化一个Git仓库，使用git init命令。

    添加文件到Git仓库，分两步：

    使用命令git add <file>，注意，可反复多次使用，添加多个文件；

    使用命令git commit -m <message>，完成。

    要随时掌握工作区的状态，使用git status命令。

    如果git status告诉你有文件被修改过，用git diff可以查看修改内容。


    HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。

    穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。

    要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

    存区是Git非常重要的概念，弄明白了暂存区，就弄明白了Git的很多操作到底干了什么。

    没弄明白暂存区是怎么回事的童鞋，请向上滚动页面，再看一次。

    那怎么提交第二次修改呢？你可以继续git add再git commit，也可以别着急提交第一次修改，先git add第二次修改，再git commit，就相当于把两次修改合并后一块提交了：

    第一次修改 -> git add -> 第二次修改 -> git add -> git commit

    好，现在，把第二次修改提交了，然后开始小结。

    令git rm用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失最近一次提交后你修改的内容。 

    git status 十个好指令 经常用就行 


    要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；

    关联后，使用命令git push -u origin master第一次推送master分支的所有内容；

    此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；

    分布式版本系统的最大好处之一是在本地工作完全不需要考虑远程库的存在，也就是有没有联网都可以正常工作，而SVN在没有联网的时候是拒绝干活的！当有网络的时
    候，再把本地提交推送一下就完成了同步，真是太方便了！

    要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。

    Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。

    查看分支：git branch

    创建分支：git branch <name>

    切换分支：git checkout <name>或者git switch <name>

    创建+切换分支：git checkout -b <name>或者git switch -c <name>

    合并某分支到当前分支：git merge <name>

    删除分支：git branch -d <name>


    修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；

    当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场；

    在master分支上修复的bug，想要合并到当前dev分支，可以用git cherry-pick <commit>命令，把bug提交的修改“复制”到当前分支，避免重复劳动

    开发一个新feature，最好新建一个分支；

    如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除。    



    git 学习网站  https://www.liaoxuefeng.com/wiki/896043488029600/898732864121440  


    关联github 库 

    一定要先拉取  然后 push  


    多人开发 

    查看远程库信息，使用git remote -v；

    本地新建的分支如果不推送到远程，对其他人就是不可见的；

    从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；

    在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；

    建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；

    从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。 


    参与开源 

    在GitHub上，可以任意Fork开源仓库；

    自己拥有Fork后的仓库的读写权限；

    可以推送pull request给官方仓库来贡献代码。


    忽略某些文件时，需要编写.gitignore；

    .gitignore文件本身要放到版本库里，并且可以对.gitignore做版本管理！



    查看 提交历史 

    git    log   会显示全信息  
    git log --pretty=online;这里会显示单条完整信息
    //配置别名
    git config --global alias.st status
    //配置log 命令
    git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

    不加--global  config 文件配置在用户主目录下面的.gitconfig中 
    加了就配置在.git/config文件中

    关于用户主目录
    直接 cd  就可以 
    然后pwd 就知道用户主目录在哪里了


    //创建一个分支 dev 

    git checkout -b +分支名
    相当于 git branch dev 
          git checkout dev


        关于分支

        1.1：git branch 
            //不加参数就是查看当前分支
            //添加参数就是创建新分支 

        1.2：git branch -d  +分支名称
             git branch -D <name>  //强行删除
            //删除分支 

        1.3：切换分支
            git  checkout +分支名称

        1.4：合并分支
            git merge +分支名称

            1.4.1
                分支合并往往不是一帆风顺的，也存在很不顺利的情况 
                有冲突很正常，你需要解决冲突然后再次提交 提交会提交给当前分支，之前的依然没有

            1.4.2
                分支合并情况 
                使用指令
                    git log --graph 可以看到当前分支合并情况
                    git rebase 可以让提交分支线编程直线
            1.4.3
                分支合并 不使用fast-forword模式 
                使用 --no-ff 形式

            
        1.5：创建并切换分支
            git checkout -b +分支名称


        分支开发策略
            在实际开发中，我们应该按照几个基本原则进行分支管理：
                master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

                干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本


    


    
    


