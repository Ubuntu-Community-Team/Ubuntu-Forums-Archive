---
title: "Have Debian want Ubuntu"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by golfncurl on 2007-10-18
I have a computer with Debian installed on it and I just purchased 
The Ultimate Ubuntu Package

[http://www.thelinuxstore.ca/index.php?main_page=product_info&products_id=1399](http://www.thelinuxstore.ca/index.php?main_page=product_info&products_id=1399)

I tried to install the Ubuntu package that came with the book and it won't install.

I can log into the root of the debian package, but that's about it.

I'm hoping the Ubuntu is easier to use.

So how do I remove Debian in order to install Ubuntu?

---

### Post by Pumalite on 2007-10-18
You can install on top of it.

---

### Post by llamakc on 2007-10-18
Back in the Warty days I switched from Debian to Ubuntu by merely changing my sources.list file. I doubt that's feasible nowadays.

---

### Post by overdrank on 2007-10-18
> **golfncurl said:**
> I have a computer with Debian installed on it and I just purchased 
The Ultimate Ubuntu Package

[http://www.thelinuxstore.ca/index.php?main_page=product_info&products_id=1399](http://www.thelinuxstore.ca/index.php?main_page=product_info&products_id=1399)

I tried to install the Ubuntu package that came with the book and it won't install.

I can log into the root of the debian package, but that's about it.

I'm hoping the Ubuntu is easier to use.

So how do I remove Debian in order to install Ubuntu?

Hi and welcome, download a live cd from here
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)
Use these two links
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And read the sticky's here
[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)
And you are ready !!!!!!!!
Good luck! :guitar:

---

### Post by golfncurl on 2007-10-18
I have a couple of live CD's but I can not boot.
The CD comes up and it says install Linux. I hit return and it starts to load then I get a blinking cursor on the top left of the screen.
At the bottom I get the following gibberish to me

Int 14: CR2 sf800000  err 00000000 EIP c020c384 cs 00000060
flags 00010007 
Stack:  c00f7d50 co3f129b c0371d8c c00f7d59 000f7d50 00000000 00000000

How do I get it to load from the cd without installing or how do I get it to install.

With no cd in it will install and load Debian GNU/Linux 3.1 

I remember the root login can I log in as a super user 

How do I completely remove Debian 3.1 and start from scratch?

---

### Post by Duck2006 on 2007-10-18
You can download gparted and format and partition your drive with that.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by golfncurl on 2007-10-19
Ok, I figured out delete all of the partitions.
I put the Live CD in and I get the Ubuntu start page.
I hit enter to install it begins to install the Linux then

Blinking curser at the top left and

Int 14: CR2 df800000 err 00000000 EIP c020c384 CS 00000060 flags 00010007
Stack: c00f7d50 c03f129b c0371dc8c 00000002 c00f7d50 00000000 00000000

Does this mean anything to anyone?

I was really hoping Ubuntu was going to be an easy.

---

### Post by kerry_s on 2007-10-19
what are your specs?
type of machine?
the error implies that you have a hardware issue.
debian is better for older machines, ubuntu drops support for older stuff.
try a current stable version, burn as a image at 4x for the best results.
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

---

