---
title: "cant load ubuntu 5.10 on 440CDX toshiba laptop .. help"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by mattix on 2007-01-06
Brother in law gave me ubuntu 5.10 (Breezy Badger?!). I tried to load it on my 440CDX toshiba laptop . I went through the default set-up procedure . When I get to " install base system" the computer loads about 90% , then returns the error message :" initrd-tools failed to load . A couple of times it loaded but then failed after selecting which kernel to use . (I tried all three) . I have a 10GB hard-drive , but only 32MB RAM . Can anyone help ? thanks......

---

### Post by jvc26 on 2007-01-06
Your RAMs the problem - you need 256 to get Ubuntu up and ticking, and 32 may well be too small for Xubuntu - I would recommend you take a peek at Fluxbuntu (apparently even lower requirements) but that may be a sticking point - have a look at Xubuntu and Fluxbuntu and see if they may fit the bill. Also 6.10 is the newest version so it may well be worth getting a 6.10 Xubuntu or a Fluxbuntu and trying them out - I'd have a bit of a read about whether any of them will work with 32Mb RAM.
Il

---

### Post by ieee488 on 2007-01-06
Others are going to tell you to install more RAM.

Or try something like PuppyLinux.

---

### Post by benuski on 2007-01-06
192 MB of RAM is the traditional minimum for any Linux system running with the X Windows System, aka graphics.   You might be able to run the basic server edition, without the X Windows system, on your computer.  I would also check out Damn Small Linux, which can run on as low as 16 MB of RAM, and has a graphical user interface.

---

### Post by dannystaple on 2007-01-06
I did a bit of a google on the laptop. If it is the one I found - based upon a Pentium 1 - 133Mhz with MMX and only 32Mb, I am not sure that Ubuntu is the right Linux distribution for it. You will maybe want to consider Puppy Linux for something that small.
Breezy Badger, 5.10 is now rather old, and therefore I would recommend a newer one. You could try Xubuntu on something that small, but according to the requirements are probably more so. 
Other threads on ubuntu requirements - and low spec workarounds:
[http://www.ubuntuforums.org/showthread.php?t=186345]("http://www.ubuntuforums.org/showthread.php?t=186345")
[http://www.mail-archive.com/xubuntu-devel@lists.ubuntu.com/msg01196.html]("http://www.mail-archive.com/xubuntu-devel@lists.ubuntu.com/msg01196.html")

About Puppy Linux:
[http://www.puppylinux.org/user/viewpage.php?page_id=1]("http://www.puppylinux.org/user/viewpage.php?page_id=1")

Good luck.
Cheers,
Danny

---

### Post by ieee488 on 2007-01-06
I agree about going with at least Ubuntu 6.06 if you decide to put more RAM into the laptop.

I started out with Ubuntu 5.10 because it came with the book I bought but there were two or three things with it that did not that work out of the box. No such problems with Ubuntu 6.06

I tried PuppyLinux on my Toshiba 2065CDS. It was okay but  seemed a bit too "cartoony" for me.

---

### Post by Bachstelze on 2007-01-06
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

is the way to go on such a machine. You could also hunt for an older Debian release - I'm running Potato on 90 MHz/ 16 MiB of RAM but the installer might be a tad more confusing.

---

