---
title: "Installing lesstif"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by cl3ellio on 2006-05-04
Hi,

Getting into Ubuntu for the 1st time over the last couple days. I'm trying to install Geomview, a viewer I need for a project, and there's several things I need to install. One is lesstif, I run the the configure file and it kicks out stating:

checking size of long long... 8
checking for X... no
checking whether gethostname() is available... yes
checking for Xt Revision Number 6... no
checking for Xt Revision Number 5... no
configure: error: You must have X11 Revision 5 or higher to compile Lesstif

But I'm almost positive that I have X11R6, so what the heck is going on? Has anyone had any experience installing lesstif or even geomview on ubuntu?

Thanks,
Chris

---

### Post by nanotube on 2006-05-04
good news - geomview is available in the ubuntu repositories. 
just run 
```
sudo apt-get install geomview
```
and it should be all good. should pull in all the dependencies automatically, too.

---

