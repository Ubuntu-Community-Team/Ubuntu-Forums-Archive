---
title: "Don't understand how to install gaim beta 4"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-10-28
Hello I am running on Kubuntu Edgy.

I followed the instructions here
[http://ubuntuforums.org/showthread.php?t=280739&highlight=gaim+beta+4](http://ubuntuforums.org/showthread.php?t=280739&highlight=gaim+beta+4)

I open konsole and get this

> maddbaron@baronworks:~$ sudo dpkg -i gaim_2.0.0+beta4-1ubuntu0_i386.deb gaim-data_2.0.0+beta4-1ubuntu0_all.deb
Password:
dpkg: error processing gaim_2.0.0+beta4-1ubuntu0_i386.deb (--install):
cannot access archive: No such file or directory
dpkg: error processing gaim-data_2.0.0+beta4-1ubuntu0_all.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
gaim_2.0.0+beta4-1ubuntu0_i386.deb
gaim-data_2.0.0+beta4-1ubuntu0_all.deb

I have gaim beta 4 tgz on my desktop and I have it unzipped in a folder on my desktop which is

/home/maddbaron/Desktop/gaim-2.0.0beta4.tar.gz

and


/home/maddbaron/Desktop/gaim-2.0.0beta4

Can someone tell me step by step instructions on how to get it installed please? I have never compiled a program before. And the install instructions are rather confusing.

---

### Post by John.Michael.Kane on 2006-10-28
Heres thread with a beta4 deb for i386 [http://ubuntuforums.org/showthread.php?t=280488&highlight=Gaim+2.0+beta+4+debs](http://ubuntuforums.org/showthread.php?t=280488&highlight=Gaim+2.0+beta+4+debs)

unpack it,and double click  the deb file.

---

### Post by maddbaron on 2006-10-28
Thank You!

---

### Post by ThrobbingBrain66 on 2006-10-28
in case you still wanted to know, you have to type
```
 cd Desktop 
```
to get to the desktop.  Then you can "dpkg -i" the files.

---

