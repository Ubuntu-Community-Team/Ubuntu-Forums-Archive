---
title: "connect to svn from remote"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-03-07
How to connect remotely and initially check out
--------------------------------------------------------------------



Hello,

1) I have successfully setup a repository in home/svn/myproject and made svn listen 

2) I have imported files to it successfully 

3) I can check out locally with > $ svn checkout file:///home/svn/myproject targetfolder


PROBLEM:
--------------
If I try to check out from another computer (I established the connection via putty, ssh, logged into the computer with the repository) and use the following command


```
$ svn co svn://192.168.0.38/svn/myproject targetfolder --username ben3
```
```
$ svn co svn://localhost/svn/myproject targetfolder --username ben3
```

But this produces the error: "No repository found in svn://192.168.0.38/svn/myproject

QUESTION:
---------------
What is the correct command to connect and then to checkout from the svn remotely?

Ben

---

### Post by luisromangz on 2008-03-07
So you are trying to make a checkout on the machine you are connecting to using ssh? Not in the one you are locally using? Then you should try the same command you used in that machine locally, 

svn checkout file:///home/svn/myproject targetfolder

---

### Post by ben22 on 2008-03-07
> **luisromangz said:**
> So you are trying to make a checkout on the machine you are connecting to using ssh? Not in the one you are locally using? Then you should try the same command you used in that machine locally, 

svn checkout file:///home/svn/myproject targetfolder

Well, this command I can execute remotely, BUT it creates a working copy on the computer where the repository resides.

What I need is:
- to connect from another machine to the repository
- create a working copy on the machine I connect from, think I need  to use svn:// for that (not using webdav)

---

### Post by ben22 on 2008-03-07
A short update:
-------------------


Hello,

I can now check out to a remote machine using Tortoise.
- I mark a folder to be used for the local working copy and click "Checkout" in the context menu appearing on right click.
- I enter: svn+ssh://ben3@192.168.0.38/home/svn/myproject
- It asks the psw for ben3 twice 
- I enter password twice.
- It checks out and creates a local copy.


Now to the persisting problem:
-------------------------------------
- I use putty, ssh
- I login first with ben3, enter the password for ben3
- Then I enter: 

 svn co svn+ssh://ben3@192.168.0.38/home/svn/myproject BBBB
ben3@192.168.0.38's password:
ben3@192.168.0.38's password:
A    BBBB/bewegtesbild
A    BBBB/bewegtesbild/sbf
A    BBBB/testsvnfolder
A    BBBB/eigen
A    BBBB/eigen/trunk
A    BBBB/eigen/trunk/test
A    BBBB/eigen/branches
A    BBBB/eigen/tags
Checked out revision 3.

It checks out into a folder BBBB, BUT on the machine where the repository is, not the remote machine.

I was wondering now whether I somehow have to define the path BBBB differently like
 svn co svn+ssh://ben3@192.168.0.38/home/svn/myproject   [http://192.168.0.35/C:/IBBBB](http://192.168.0.35/C:/IBBBB) ???

The problem is that this is not working and how would I define the path if the remote machine uses Windows as OS?

Cheers,
Ben

---

