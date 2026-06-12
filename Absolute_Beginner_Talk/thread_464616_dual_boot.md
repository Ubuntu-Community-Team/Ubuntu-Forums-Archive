---
title: "dual boot"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by timelord29 on 2007-06-04
how do i set up a dual boot between ubuntu and windows xp? i do not want to format and partition a hard drive. i have 2 hard drives, one with windows already on it and one that im gonna install ubuntu on shortly. how do i set it up so when i start up my computer, it gives me an option to chose what OS i want to boot off of?

---

### Post by FleetAdmiral74 on 2007-06-04
I believe just installing ubuntu default will work, should recognize the xp partition (dont erase it!), and on boot you can choose. Xp is at bottom of the list though, ub on top. Certainly ways to change that though, im not sure how.

---

### Post by Inxsible on 2007-06-04
Make sure your XP disk is attached so that the grub can put an entry for it in the menu. Also make sure you do not format it while using GParted.

---

### Post by Marious on 2007-06-04
Feisty is great when it comes to this, it should recognize your partition of windows xp so no worries there. If I am not mistaken if you use the second hard drive just let it do a default install on that hard drive alone and it will partition it for you, unless you have data on that disk which you should back up if you do. If you do not have data then you are good to go and you should just allow it to do the partitioning if you do not feel comfortable doing it yourself, or you can look at one of the many guides out there, and what folks recommend for your various partitions, as usual your important partitions are swap, /, and I would do one for home and give it a hefty chunk if you have any plans on doing big downloads of any kind. You will also find that you will wish to create a Fat32 partition if you want to share it between Ubuntu and windows, I have a like 80G partition to share between them. Enjoy I love Ubuntu and many folks here will agree with me on that.

Marious

Edit: Yeah as mentioned in the above post Grub is your friend and you should check the file to ensure that it see's windows and that it is listed.

---

### Post by timelord29 on 2007-06-05
no i do NOT want 2 partitions. i have 2 seperate hard drives and there both plugged into the computer. i want the option of choosing which hard drive to boot of off at startup. i do NOT want to bother with partions and risk losing everything. i dont have the best luck with computers xD.

---

### Post by ccfjeff on 2007-06-05
> **Marious said:**
> You will also find that you will wish to create a Fat32 partition if you want to share it between Ubuntu and windows...

I believe that Linux can now safely read and write to NTFS partitions as well:


[COLOR="DarkRed"][SIZE="4"]NTFS-3G Read/Write Driver[/SIZE]
Updated: June 1, 2007

[http://www.ntfs-3g.org/]("http://www.ntfs-3g.org/")

*Over a million hits since the stable driver release*


The NTFS-3G driver is an open source, freely available read/write NTFS driver for Linux and other operating systems. It provides safe and fast handling of the Windows XP, Windows Server 2003, Windows 2000 and Windows Vista file systems. Most POSIX file system operations are supported, with the exception of full file ownership and access right support.

The purpose of the project is to develop, continuously quality test and support a trustable, feature rich and high performance solution for hardware platforms and operating systems whose users need to reliably interoperate with NTFS. Besides this practical goal, the project also aims to explore the limits of a hybrid, kernel/user space file system driver approach. Performance, reliability and feature richness per invested effort are being examined.

The driver is in STABLE status. Please see our test methods and testimonials on [the driver quality page]("http://www.ntfs-3g.org/quality.html")...
[/COLOR]

There is a HOWTO in the Ubuntu forums:  [http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by confused57 on 2007-06-05
> **timelord29 said:**
> no i do NOT want 2 partitions. i have 2 seperate hard drives and there both plugged into the computer. i want the option of choosing which hard drive to boot of off at startup. i do NOT want to bother with partions and risk losing everything. i dont have the best luck with computers xD.

Here's a possible option:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by pagal on 2007-06-05
But then I am wondering, how about the other way?

I installed Ubuntu 7.04 for a week or so on my 1.5GHz laptop. Running like a charm.
But since im not completely in to the linux/ubuntu-experience yet, I would like to re-install winxp(yes i know, but bare with me) due to games like WoW.
I am not running any ATI or nVidia gfx card, just this generic card attached or implemented to my motherboard, so many of the HOWTOs doesn't seem to apply to my gfx card.

My question is this; can I re-install WinXP from this Ubuntu-partition and make a dual-boot?

---

### Post by pagal on 2007-06-05
Oh yes.
I have tried Wine, but it doesnt get me very far.

---

