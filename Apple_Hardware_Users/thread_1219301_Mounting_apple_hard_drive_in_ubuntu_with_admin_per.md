---
title: "Mounting apple hard drive in ubuntu with admin permissions"
date: 2009-07-21
forum: Apple Hardware Users
---

### Post by Rawjava on 2009-07-21
I would like to mount it as my account on mac. im running leapord 10.5.7 and ubuntu 8.10.
The ubuntu is an ext3 partition.

i can mount it i just cant access many folders on it so i would like to use it without so many restrictions.

---

### Post by fbugnon on 2009-07-27
This is probably due to the fact that your Ubuntu-user is not seen as the same user you have in Mac, even if they have the same name, because they don't have the same UID.

In other words, your Ubuntu-user is not the owner of the files created with your Mac-user.

For further info (and solution) on this, take a look at:

[http://ubuntuforums.org/showthread.php?t=852144&highlight=uid+mac+home](http://ubuntuforums.org/showthread.php?t=852144&highlight=uid+mac+home)

and 

[http://ubuntuforums.org/showthread.php?t=1152183&highlight=uid+mac+home&page=2](http://ubuntuforums.org/showthread.php?t=1152183&highlight=uid+mac+home&page=2)

Hope it helps.

---

### Post by Rawjava on 2009-07-28
Can i add another partition so it acts like my sharing folder?

---

### Post by fbugnon on 2009-07-28
I think the second link on the last post it's exactly about this (using a share folder for both systems).

---

