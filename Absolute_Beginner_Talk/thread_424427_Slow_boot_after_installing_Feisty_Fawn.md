---
title: "Slow boot after installing Feisty Fawn"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by mike4477 on 2007-04-26
Just installed Feisty Fawn as upgrade from Edgy Eft.  My boot process now takes over five minutes.  Attached is my Bootchart file.  Thanks for your help.

---

### Post by justin whitaker on 2007-04-27
Good lord! 

Ok, if I read this correctly, the system boots, launches busybox and modprobe...and sits there for 45seconds. On my clean install, I'm to the desktop in 45 seconds. 

Then it loads the restricted modules, sets leyboard, etc....and chokes at evms. I have no experience with this, but do you really need EVMS? 

[http://evms.sourceforge.net/](http://evms.sourceforge.net/)

What are the benefits to a desktop user?

Here is what I would do: submit a bug, since there seem to be 1400+ posts on EVMS when I searched the forums, and either reinstall, or try recompiling the kernel without EVMS.

---

### Post by mike4477 on 2007-04-30
Update - - 

I was having two main problems when I posted this original request for help:

1) The boot problem I discuss in this thread

2) When I tried to reinstall using the the Feisty Fawn CD I hung at a blank screen after I selected the install option.

Since I had orignally gone through the dapper - edgy - feisty upgrade path I always assumed something had become corrupted along the way.  So yesterday I went out and bought a new hard drive, tried to install using the Feisty Fawn CD and had the same blank screen problem.  

I assume this means Feisty is having problems with my hardware and I'm just going to have to wait for an update or the next Ubuntu release and hope it works.  I'm trying to install on a Dell GX260 with a Pentium 4 2.0 GHz and 512M of RAM.  

Am I missing something here?

---

