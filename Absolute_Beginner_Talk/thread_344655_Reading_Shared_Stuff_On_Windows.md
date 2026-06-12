---
title: "Reading Shared Stuff On Windows"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2007-01-23
Hi,
I am on a class C network, which is predominantly windows. I shared some of my folders using NFS, but i am not able to read them on any other comps, wen i try to it asks me a password wen i put my root user and password it dowsnt accept it??

How To share stuff for windows clients properly is my question??

---

### Post by Wes24 on 2007-01-23
You'll need samba to share files on a windows network. You can install samba using the following command:

sudo apt-get install samba smbfs

Then, right-click on the files you want to share and it'll ask whether you want to use NFS or SMB to share the file. Choose SMB.

---

### Post by AdyE on 2007-01-23
[http://www.ubuntuforums.org/showthread.php?t=228454&highlight=how+to+share+a+folder+with+windows+xp+on+home+network](http://www.ubuntuforums.org/showthread.php?t=228454&highlight=how+to+share+a+folder+with+windows+xp+on+home+network)

This forum post was very helpful :-)

---

