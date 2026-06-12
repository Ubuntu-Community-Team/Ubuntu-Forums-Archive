---
title: "double boot BSD and Ubuntu Server"
date: 2007-01-18
forum: BSD
---

### Post by arkangel on 2007-01-18
I got a New PC (AMD 64)   and I want to install a double boot using freeBSD and ubuntu server ,  any of you have tried such thing.  It is dificult? there is a tutorial  etc

---

### Post by mips on 2007-01-18
arkangel,

I asked a similair question on irc in #openbsd. They recommended I use **[GAG]("http://gag.sourceforge.net/")**

I run openbsd on my laptop in a dualboot config with Windows XP.

GAG is the easiest thing to setup, you cannot believe how easy it is. All graphical.

Just download the small .iso image of gag and install it.

You could also use grub, there are many guides out there or just read the excellent bsd documentation.

---

### Post by runningwithscissors on 2007-01-20
> **arkangel said:**
> I got a New PC (AMD 64)   and I want to install a double boot using freeBSD and ubuntu server ,  any of you have tried such thing.  It is dificult? there is a tutorial  etc

The only difficult part is the one people are always wary of. Resizing a live partition.

If you have a free partition, it is as simple as booting up the CD, selecting the relevant options from the installer and booting into your new FreeBSD install.

---

### Post by the_darkside_986 on 2007-02-15
I am not so sure about the server environment but on my PC, I have them sharing my one and only hard drive.

First, I have Ubuntu installed. We all know what the menu.lst in the grub configuration folder looks like for booting Ubuntu. But FreeBSD, I had to look that one up and it was easy:

# For booting FreeBSD 

title FreeBSD 
root (hd0,a) 
kernel /boot/loader 
boot

I added that entry to the bottom of menu.lst in /boot/grub. (In Ubuntu, of course)
Of course, I told the freeBSD installed NOT to overwrite my MBR because I wanted to manually edit the grub file because I did not want to lose access to Ubuntu since I can't get internet or sound working in freeBSD.
I don't understand why hd0,**a** works but for some strange reason it does. I guess it is because I let FreeBSD walk me through the installation and I just did what the screen said to do. (Nothing at expert level)

---

