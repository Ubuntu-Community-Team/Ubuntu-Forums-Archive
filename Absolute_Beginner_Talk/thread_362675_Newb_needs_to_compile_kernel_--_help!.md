---
title: "Newb needs to compile kernel -- help!"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Dusty Chalk on 2007-02-15
The questions:

I have an ancient Sony Vaio PCV-RX550/-7732 (256M upgradeable to 512M, just to give you an idea), with a more recent vintage graphics card (PNY GeForce 6200) which I use with a 22" widescreen LCD, so I need widescreen mode.  So I went to the NVidia site and downloaded their program, and it guided me through looking for one, didn't find one, so it needs to compile one.  So I used aptitude to get the libc6, gcc, cpp, make &c. packages, and now it says it needs the source for the kernel.  Makes sense, as it needs to compile a driver into it, but...how?  I tried downloading the linux-source module, but all I found on my computer was a copyright and a text file...did it put it somewhere else?  Where did it put it?  Is this going to be adequate, or do I need specifically the source code of all the modules used to compile my particular flavour of ubuntu linux (6.06 w/gnome)?  I read something about deb and apt-get...is there a way I can "trick" aptitude into getting the source for me -- I didn't see "getting the source" as an option anywhere in there.  Is there a better way for my computer to go through the modules I have an just get the source for all of them (I have plenty of disk space)?  Should I go back to my old graphics card?  I got the new one because in Windows, the driver for the old one was no longer supported and there was no widescreen mode.

Background:

I'm not a newb to the software world, but I'm new to linux.  I have a lot of experience with unix -- mostly Solaris -- and I'm a software engineer, and I've done a lot of system administration, so a lot of this is not foreign to me.  But that was a long time ago and times have changed.  All this "package installer" stuff was just beginning to creep into the Solaris install.

I just installed linux for the first time on the above computer -- took out the hard drives and placed two new blank ones in.  So I'm pretty happy with myself that I got it running at all -- there was no guarantee that it was going to work.

Thanks in advance for any help you'all can give me!

---

### Post by Dusty Chalk on 2007-02-15
Never mind, I think I found it [here](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2).  I'll post again if it works and I move on to my next problem, or it doesn't work.

To apologize for my newbness, I submit [this funny YouTube clip](http://www.youtube.com/watch?v=eRjVeRbhtRU).

---

### Post by Bachstelze on 2007-02-15
All you need to know about installing the nvidia driver is [here](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia).

Good luck ;)

---

### Post by Dusty Chalk on 2007-02-15
Sweet!  Thank you...

---

