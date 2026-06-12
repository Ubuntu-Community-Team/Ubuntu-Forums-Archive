---
title: "HELP with sudo gedit /etc/X11/xorg.conf"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by wtfdop0987 on 2007-07-04
I need help with editing my xorg.conf file;;;  sudo gedit /etc/X11/xorg.conf...i goto terminal:

s@Samuel:~$ sudo gedit /etc/X11/xorg.conf
Password:

i dont know why it requests a password, i am the administrator and i installed ubuntu...the thing is it wont let me type a password....i click enter with nothing entered and it goes back to:

 
s@Samuel:~$

---

### Post by forestpixie on 2007-07-04
it's entering password - you just can't see it - put it in and enter

---

### Post by tgoose on 2007-07-04
It's a security measure. You are **not** the administrator because then, if you ran any malware, it would be able to break your entire computer (much like on Windows). The password for sudo is your normal user password, and it temporarily gives you the powers of the real administrator (called "root" on Linux systems.) You can't see it by typing, but it is there.

There is no way by default of logging in as root on Ubuntu; you can only gain powers temporarily.

See [http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

---

### Post by overdrank on 2007-07-04
> **wtfdop0987 said:**
> I need help with editing my xorg.conf file;;;  sudo gedit /etc/X11/xorg.conf...i goto terminal:

s@Samuel:~$ sudo gedit /etc/X11/xorg.conf
Password:

i dont know why it requests a password, i am the administrator and i installed ubuntu...the thing is it wont let me type a password....i click enter with nothing entered and it goes back to:

 
s@Samuel:~$

HI I believe you need to use this command
[HTML]gksudo gedit /etc/X11/xorg.conf[/HTML]
Good luck and remember to backup your xorg before changes. ;)

---

### Post by wtfdop0987 on 2007-07-04
i entered my password and it goes back to s@Samuel:~$

---

### Post by tgoose on 2007-07-04
> **wtfdop0987 said:**
> i entered my password and it goes back to s@Samuel:~$
Does it not open a gedit window in the background? If not, try what overdrank suggested.

---

### Post by wtfdop0987 on 2007-07-04
i press enter after i type in gksudo gedit /etc/X11/xorg.conf and it doesn't even give me a place for password, it goes back to s@Samuel:~$

---

### Post by overdrank on 2007-07-04
> **wtfdop0987 said:**
> i press enter after i type in gksudo gedit /etc/X11/xorg.conf and it doesn't even give me a place for password, it goes back to s@Samuel:~$

HI which version of ubuntu are you using?

---

### Post by wtfdop0987 on 2007-07-04
Ubuntu 7.04

---

### Post by AlexenderReez on 2007-07-04
> **wtfdop0987 said:**
> I need help with editing my xorg.conf file;;;  sudo gedit /etc/X11/xorg.conf...i goto terminal:

s@Samuel:~$ sudo gedit /etc/X11/xorg.conf
Password:


ubuntu version 7.10 

> reez@aLeXeNdeRreEz:~$ sudo gedit /etc/apt/sources.list
[sudo] password for reez:


cool right?hm...sorry for ask stupid question..are you sure you have gedit installed?...gedit is installed by default but maybe you have remove gedit without realized it...so try...

> sudo apt-get install gedit &&  sudo gedit /etc/X11/xorg.conf

---

### Post by wtfdop0987 on 2007-07-04
> **reez0105 said:**
> ubuntu version 7.10 



cool right?hm...sorry for ask stupid question..are you sure you have gedit installed?...gedit is installed by default but maybe you have remove gedit without realized it...so try...

still goes back to s@Samuel:~$  without password dialouge or box opening in background

---

