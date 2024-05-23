# GIT

用c写的分布式版本管理系统

GitHub网站为开源项目提供Git存储

分布式版本控制系统意味着每个人的电脑上都有独立的版本库，即使离线也可以先提交到本地版本库，联网之后再进行版本交换

​	引申出的问题：当远程版本与本地不一致时，尝试push会提示先拉取。可以通过强制推送解决git push -f



版本回退：git会记录commit id，可以通过git reset命令回退到一个具体的版本，也可以直接使用HEAD^来回退到上一个版本（父节点？）

​	会先修改指针，然后更新工作区文件。



回退之后，git log版本库中子节点的记录会被隐藏，但是仍然可以通过git reflog找到这些节点的id，从而回退到这些“未来”的版本



git是如何存放这些版本快照的？直接把一个版本的所有文件存在.git目录下显然不行，对空间的需求太大了

​	解决：git 是一个基于更改的版本控制系统，它跟踪的是文件的修改，包括添加、删除、修改的行，这节约了很多空间。



git init的时候会自动创建一个分支master

​	我实际上使用时好像默认创建的分支叫main？

什么是分支?

​	我的理解：分支就是用于多人合作时，不同的工作互不干扰，a、b各写一个不同的组件，就各自创建自己的分支，使得自己未完成的代码不影响其他分支的测试，都开发完以后进行合并



工作区指git init下的整个目录，在工作区修改后，git add将修改后的具体文件提交到.git下的暂存区（stage），git commit将暂存区部分提交到分支（如master）



git checkout -- file（文件名）可以将该文件撤销回最近一次git commit或git add时的状态（即撤销回版本库状态或暂存区的状态）



除了撤销工作区状态，有时候还要撤销暂存区的修改，可以使用git reset HEAD file，在回滚命令后添加具体的文件名



尝试创建远程仓库，使用github托管

遇到问题：上传rsa密钥后仍然不能通过密钥验证

在一篇博文：https://blog.csdn.net/yuzhiqiang_1993/article/details/127032178

和github官方文档：https://docs.github.com/zh/authentication/troubleshooting-ssh/using-ssh-over-the-https-port

中找到了解决方法



