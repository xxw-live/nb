# git学习笔记

**（思路：github上的仓库用ssh来clone到本地，再修改user.name etc、config里面的url改为https）**

## 一、如何clone（多账户）

### 1、将公匙添加到本地

 	**如果没有添加**

![image-20220803210251375](C:\Users\nesv\AppData\Roaming\Typora\typora-user-images\image-20220803210251375.png)

​	1、ssh -T git @github.com             (前面的git是不变的，后面的github是改为你自己设置的host，比如我的github2)

​			这一步其实没什么用主要是看你本地有无存储私匙

​	2、ssh-agent bash

​			启用ssh agent(大概)

​	3、ssh-add ~/.ssh/id_rsa_xxxxxx

​			添加ssh私匙到里面（酱紫才能clone)

这次可见的是

![image-20220803183113835](C:\Users\nesv\AppData\Roaming\Typora\typora-user-images\image-20220803183113835.png)

clone图片

![image-20220804121337835](C:\Users\nesv\AppData\Roaming\Typora\typora-user-images\image-20220804121337835.png)



## 二、如何push

**问题在于上面的搞好了以后不知道为啥好像不能退出，可能ssh多仓库bug**

### 1、修改url、以及user.name etc

**将ssh链接修改为https链接**	

​	在.git 下面的config 文件里面修改（**蓝色字体样式**）

![image-20220804130015866](C:\Users\nesv\AppData\Roaming\Typora\typora-user-images\image-20220804130015866.png)

然后ok了

### 2、死方法（bug？）

重复clone的步骤建立ssh链接

然后再push

![image-20220804121801068](C:\Users\nesv\AppData\Roaming\Typora\typora-user-images\image-20220804121801068.png)









# git pull问题

因为我在本地删除了文件，而远程上并没有进行修改；所以git pull并不会更新本地，只能强制合并来达到强制更新本地；当我在远程仓库新建一个文件的时候，git pull 就会更新本地了。

简而言之，git pull发现有新的版本号才会执行更新，比如你版本号是1，git上没有新的版本号，无论你在本地干了什么，除了push改变版本号，你Git pull等于没用。