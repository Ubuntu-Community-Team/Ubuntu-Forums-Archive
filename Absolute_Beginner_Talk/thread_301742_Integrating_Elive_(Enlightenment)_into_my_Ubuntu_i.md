---
title: "Integrating Elive (Enlightenment) into my Ubuntu install"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by pastorjay on 2006-11-17
Is there a way to integrate the Enlightenment desktop into ubuntu?  I have some issues trying to use the Elive Live CD, so I am trying to find a work around to be able to install it.

---

### Post by justin whitaker on 2006-11-17
> **pastorjay said:**
> Is there a way to integrate the Enlightenment desktop into ubuntu?  I have some issues trying to use the Elive Live CD, so I am trying to find a work around to be able to install it.

I don't know if anyone has created E17 debs yet, but you could grab the whole mess from source or CVS and compile it.

[http://www.enlightenment.org/Enlightenment/Get_Enlightenment/](http://www.enlightenment.org/Enlightenment/Get_Enlightenment/)

Part of the issue with Elive is that it's unstable, uses a hack modular ubuntu (DSS), and is more focused on the GUI than fixing some of the hardware issues.

---

### Post by pastorjay on 2006-11-17
Well, I do like the interface.  I have downloaded the live cd, and it installs fine on an older compueter (nf2 box), but I cannot get it to load on my C2D Gigabyte DS3 box or on my e1705 laptop.  I get this error:
/bin/sh: can't access tty; job control turned off

I cannot find any fixes for that.  I am sure it is one of those hardware incompatabilities.

---

### Post by groggyboy on 2006-11-17
If you want to use the Enlightenment window manager with your ubuntu install, try [this HowTo]("http://www.ubuntuforums.org/showthread.php?t=20216") on the forums.  If you jump to the end, apparently some people have had issues with the repositories in the original howto.  If you check out [this website]("http://seerofsouls.com/ubuntu.html") and scroll down partway, you'll find repos for both Dapper and Edgy.  You should be able to find .debs of e17 there.

cheers!

---

