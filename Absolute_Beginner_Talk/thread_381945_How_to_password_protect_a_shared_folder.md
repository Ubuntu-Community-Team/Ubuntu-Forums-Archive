---
title: "How to password protect a shared folder"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by gtiguy on 2007-03-11
Hello all,

I'm new to linux but am learning quickly :). So what I have is one box runing ubuntu 6.06
It's running apache2 web server to host my web page and I want to use is as a main media share server.  I am able to share folders on the linux box without a user name or password by editing the smb.config file and adding the following:

[CoolWallPaper]
path = /home/erains/Cool Wall Paper
guest ok = Yes
force user = erains
read only = No
inherit acls = No
available = yes
browseable = yes
public = yes
writable = no

This is they way I share folders with my windows boxes with out a password. Now I want to add a layer of security and require the windows box to enter a user name and pass word to access the share folder.  How do I do this I've tried a few things without succes.

Any help prvided would be much appreciated thank you!

-Eric

---

### Post by gtiguy on 2007-03-11
bump for me :)

---

### Post by gtiguy on 2007-03-11
Ok figured out how to have it ask for user name and password once now I need it to ask all the time anyone?

-Eric

---

