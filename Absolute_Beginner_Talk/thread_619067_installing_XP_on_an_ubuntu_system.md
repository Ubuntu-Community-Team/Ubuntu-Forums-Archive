---
title: "installing XP on an ubuntu system?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Lagos on 2007-11-21
hey guys. 

im a brand new linux user, and im hoping you can help me out. 
i currently have gutsy installed and setup to use the full partition of my drive. now i need to also install XP.  how would i go about creating an ntfs partition and adding it to the boot loader so that i can install and dual boot to XP?

i tried searching around for any guides, but all i can find is info on how to install linux on a machine that already had a windows partition and not the other way around. 

thanks
-lagos

---

### Post by Mike Zimmer on 2007-11-21
It is better to install windows first, but since you didn't, you may be able to do the following.

1 - back up your install in you have a way of backing up a Linux partition, or at least backup your important user created/downloaded files.
2 - use a utility to resize the linux partition so that there is space (best at the start of the hard drive) for windows. There is a linux utility disk that has such a utility. It needs to be burned to CD and them used to boot from. You need to use Qparted from the disk or something like that to resized the linux partitions. You may have two, an EXT3 and a SWAP would be typical. Look for System Rescue x86 - google for it.
3 - You can then install windows, but it will probably over write your Grub boot loader code.
4 - You will need to have another bootable CD with a utility for reinstalling Grub. - Super Grub Loader - google for it.
Sorry this is terse, not very detailed, but I have used the general strategy before. It might be easier to just install XP into a partition that leaves enough on the drive for Ubuntu, and install Ubuntu again.

There may be others with a more sophisticated approach.

---

### Post by toupeiro on 2007-11-21
Lagos,

The above steps would be the  way I would do it.

[Here]("http://gparted-livecd.tuxfamily.org/") is a link to download gparted, which is what I use for resizing.

You have to leave your swap partition intact, and if you have a /boot partition, that will need to be there also, so do not resize or remove either of these two partitions.

[Here]("http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml") is the link to super grub,  This will restore your grub boot loader once you've installed XP.

You have a little work ahead of you, but it is all straightforward and safe.

If at all possible, I would consider whether or not you have the resources to run Windows XP virtualized.  The procedure would be much easier.

---

### Post by tact on 2007-11-21
Yeah actually... if you are a brand new ubuntu user and have not done too much customising etc...that it just may be better to start over and clean install XP first, then ubuntu.

Again I stress - assuming you have not done huge amounts of customising your ubuntu:
1.  ubuntu is so fast to install (compared to a full on working XP install with Office and so on)... and 

2. taking into account all the effort you will have to go to with resizing partitioning, and backing up, and to get the grub bootloader working again after XP hoses it....(all these things are tricky and take hours!)... and

3.  after using ubuntu for a short time for sure you now know a few thoughts on how you'd do things better if you reinstalled (like placing /home on a separate partition all its own ...etc.etc - this could be your chance!)

then it would be quicker and less messy to just let WindowsXP reformat the drive and start over.

Alternatively...  have you considered whether running XP in a VM would work for you?  Then no need to blow ubuntu away, no need to resize partitions, no need to back things up, no need for all that tricky time consuming activities...  Just need to:
1  Install VMware server (or qemu or virtualbox - whatever floats your boat)
2. create the VM with the specs you want to give XP
3.  install XP from original CD to the VM
4.  install your apps.

(reasons to not consider using XP in a VM - no 3D acceleration so eyecandy and flashy games wont run)

I used to dual boot ubuntu and XP...  but found I never needed to use the XP partition, and not into gaming on windows at all....  so one fine day decided to reclaim the "wasted" XP partition.  Then as a "just in case" set up XP in a VM...  Its still there gathering dust today.  hehehe

---

### Post by daengbo on 2007-11-21
Can you get away with installing XP in a virtual machine like VirtualBox? That's how I do it.

---

### Post by Lagos on 2007-11-21
thanks for the advice. you guys are awesome.

i actually did spend a fair bit of time getting getting everything to work correctly, so i didnt want to just format over this install. but i guess that might be my best option, with least downtime.  perhaps ill back up stuff like my xorg.conf and network settings so that i have less to setup again.

as far as using virtual machine... i want a full xp install for gaming, photoshop, movie maker, itunes, etc. something to help me during this transition phase.

---

### Post by tact on 2007-11-21
well since you have spent a lot of time getting ubuntu set up...  back up everything in /etc and /home (there are lots of hidden config files in /home) at the least.  It will save you lots of configuring later.

Even if you don't back up all the software you have downloaded - backing up /home will save all the individual program's configs and later when you reinstall them its like magic to find your email and other apps all configured like before.  :)

---

### Post by Dr Small on 2007-11-21
> **Lagos said:**
> thanks for the advice. you guys are awesome.

i actually did spend a fair bit of time getting getting everything to work correctly, so i didnt want to just format over this install. but i guess that might be my best option, with least downtime.  perhaps ill back up stuff like my xorg.conf and network settings so that i have less to setup again.

as far as using virtual machine... i want a full xp install for gaming, photoshop, movie maker, itunes, etc. something to help me during this transition phase.
Going back to Windows will never help you get over your transition phase with Ubuntu.....

---

### Post by BradwJensen on 2007-11-21
> **Dr Small said:**
> Going back to Windows will never help you get over your transition phase with Ubuntu.....


Very true story, Evidence was once here. haha

---

### Post by Lagos on 2007-11-21
> **Dr Small said:**
> Going back to Windows will never help you get over your transition phase with Ubuntu.....

no plans to "go back". just need it for gaming. tux racer is getting a bit stale for me. :lolflag:

---

### Post by Aquilastudio.com on 2007-11-21
Do not risk it. A system inside a system is CRAP. DOUBLE BOOT PEOPLE

---

### Post by tact on 2007-11-22
> **Aquilastudio.com said:**
> Do not risk it. A system inside a system is CRAP. DOUBLE BOOT PEOPLE

It may be "crap" for 3d accelerated games etc... or 3d eyecandy...  its not "crap"  (unqualified).

The laptop my company has me running around with is a puny Dell D410.  Its a 1.73MHz pentium M (single core) and has 1.5Gb RAM.  It is no supercharged performer.

I routinely fire up 3 VM's - each with a different Operating System - in one of my job roles...
1.  WinXP
2.  Windows Server 2003
3.  embedded linux

The above 3 are running all at the same time (on 3 different faces of the compiz cube some more!) and they communicate to each other via TCP/IP.   They are components of a solution my company delivers and I run them in VM's on my laptop to demo to customers....

Thats THREE VM's...  running at once as client/servers communicating in real time ...  on one puny laptop with Gutsy underneath it all...  

Project all that onto a big screen, then hit the Compiz Scale or Expo modes and see the 3 applications all interacting on the screen at once...  then spin the cube around a few times - makes for a really wild demo session.

Thats not crap.

ciao

---

### Post by tact on 2007-11-22
...Oh ya... and just to tease people in the office I sometimes run my own XP VM in "seamless" mode.. 

That lets me put the XP "Start Button" and panel at the bottom of my screen.   I have it "auto hide" and then when some unsuspecting colleague comes along to comment ...  perhaps asking "are you still using linux?  what happens when you want to run a windows app?"  ....  I move my mouse to the bottom edge of the screen... the XP Start Button and panel slides up from the bottom... CLick Start>All Programs>MS-Project (for example)...  and let them see it run SEAMLESSLY on my ubuntu desktop.

People are sooooo.o.o.o.o easily amazed...  *chuckle*

---

### Post by HermanAB on 2007-11-22
Hmm, the future is virtual.  Dual booting is so 20th century!

However, if you wish to play WIndows games, then you need to dual boot, because you need every last machine cycle and fancy graphical support.

Otherwise, if you need Windows to run some specific applications, then a VM is the way to go.  The advantage is that you can run Windoze in a window and doesn't have to reboot.  VMs are very fast - once installed properly, you won't notice a speed difference.

---

