---
title: "Intel iMac Dual-boot leopard/ubuntu"
date: 2008-06-18
forum: Apple Hardware Users
---

### Post by computergeek6 on 2008-06-18
I have one of the Intel iMacs, and I want to install Ubuntu on it. The problem is that I need to be REALLY sure that my data is safe. I know that you can install using Bootcamp, but how can you install the wireless drivers if there is no internet connection? If there is a tutorial on safely installing Ubuntu on an Intel iMac, please post a link to it.

---

### Post by ninjapenguin on 2008-06-18
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

That's the page I used when I installed Ubuntu on my new iMac, all of my drivers aren't working at the current moment though, mainly my wireless because of its WPA.  Also, you can install the wireless drivers from either downloading them off of OS X and putting them on a cd or flash drive or using your Mac OS X install disk to get them from the bootcamp driver section.

---

### Post by computergeek6 on 2008-06-18
Is it safe to do without backups? I know I should be backing up, but I just can't afford a backup drive.

---

### Post by ninjapenguin on 2008-06-18
> **computergeek6 said:**
> Is it safe to do without backups? I know I should be backing up, but I just can't afford a backup drive.

I did it with out a back up, but you got to make sure you use bootcamp to partition the drive, for reliability, and then when you actually have to use gparted while installing ubuntu to make the FAT32 Bootcamp partition ext 3 make sure you choose the right partition and make sure you install grub the boot loader on the right partition and not hd0.

---

### Post by computergeek6 on 2008-06-18
Thanks. I was really nervous about the data safety aspect. How would I get the drivers from OS X? Would there be compatibility issues?

---

### Post by ninjapenguin on 2008-06-18
> **computergeek6 said:**
> Thanks. I was really nervous about the data safety aspect. How would I get the drivers from OS X? Would there be compatibility issues?

You would get them off of your Mac OS X install cd that came with your iMac, and then there are a lot of helpful community documents that navigate you through installing each driver, or you can also use google and this forum if you're having issues.

---

### Post by cyberdork33 on 2008-06-18
iMac info is here, though not as pretty as the Macbook Pro info :)
[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

The easiest method for installing (dual-boot) is to use bootcamp to resize your OSX partition. Then boot the Ubuntu CD, start the partition editor (gparted) and delete the FAT32 partition your created. Then start the installer and choose to install to the largest free space.

---

### Post by computergeek6 on 2008-06-18
How would I fix the no-boot problem without installing rEFIt? Also, will the no-boot issue affect my ability to boot OS X?

---

### Post by cyberdork33 on 2008-06-18
> **computergeek6 said:**
> How would I fix the no-boot problem without installing rEFIt? Also, will the no-boot issue affect my ability to boot OS X?
the no boot issue only effects the MBR which OS X doesn't care about. So yes OSX still boots. and you don't need to boot OS X to run rEFIt. The tool is in the boot menu.

---

### Post by computergeek6 on 2008-06-18
I don't want to have to choose the OS every boot-time. Can I boot holding option, then choose, just like default Boot Camp. How can I fix the MBR without installing rEFIt?

---

### Post by cyberdork33 on 2008-06-18
> **computergeek6 said:**
> I don't want to have to choose the OS every boot-time. I want to be able to boot holding option, then choose, just like default Boot Camp. How can I fix the MBR without installing rEFIt?

1. you don't have to choose everytime. The default choice is booted automatically after a delay that you can adjust. (much like grub does).

2. You don't have to leave rEFIt installed, just use the tool, then uninstall it when all is well.

P.S. that functionality has nothing to do with bootcamp. It is part of the mac firmware.

---

### Post by computergeek6 on 2008-06-18
can i install using the installer, instead of livecd?

---

### Post by handy on 2008-06-19
> **computergeek6 said:**
> I have one of the Intel iMacs, and I want to install Ubuntu on it. The problem is that I need to be REALLY sure that my data is safe. I know that you can install using Bootcamp, but how can you install the wireless drivers if there is no internet connection? If there is a tutorial on safely installing Ubuntu on an Intel iMac, please post a link to it.

I only read ***your*** post, so this has probably already been covered; anyway if not here is a wiki page I created for Arch, which up until the Arch installation part should be helpful I hope.

***_[http://wiki.archlinux.org/index.php/IMac_Aluminium](http://wiki.archlinux.org/index.php/IMac_Aluminium)_***

---

### Post by cyberdork33 on 2008-06-19
> **computergeek6 said:**
> can i install using the installer, instead of livecd?
I don't understand what you mean. The installer and LiveCD are on the same Disc.

---

### Post by computergeek6 on 2008-06-19
I didn't have any CDROMS around, so I burned it onto a DVD, and when I boot from the disk, the live-cd option doesn't show up.

---

### Post by cyberdork33 on 2008-06-19
> **computergeek6 said:**
> I didn't have any CDROMS around, so I burned it onto a DVD, and when I boot from the disk, the live-cd option doesn't show up.
Did you download the Alternate install CD image or the normal CD image?

You can still use the alternate installer, you just have to use the manual partitioner to delete the bootcamp partition and create a root and swap partition in its place.

---

### Post by computergeek6 on 2008-06-19
I got the newest normal image, and there's no liveCD

---

### Post by cyberdork33 on 2008-06-19
The "normal" cd is a LiveCD... meaning that it boots into a Live install of Ubuntu that you can use. See attached image.

---

### Post by computergeek6 on 2008-06-19
Well, I downloaded the dual-core image, booted it, and that option wasn't there. Does the dual-core image have it too?

---

### Post by cyberdork33 on 2008-06-19
dual-core image? where are you downloading this from? There is no "dual-core" image...

---

### Post by computergeek6 on 2008-06-19
I downloaded from the ubuntu website. I mean the image that the MacBook tutorial says takes advantage of my dual-core processor.

---

### Post by cyberdork33 on 2008-06-19
> **computergeek6 said:**
> I downloaded from the ubuntu website. I mean the image that the MacBook tutorial says takes advantage of my dual-core processor.If you mean the 64bit installer, that is fine, and yes it has the same menu. I even double-checked.

---

### Post by computergeek6 on 2008-06-19
I'll boot the disk and write down all the choices.

---

### Post by computergeek6 on 2008-06-20
Here's an image of the screen: [[IMG]http://img211.imageshack.us/img211/4006/screenex2.th.jpg[/IMG]](http://img211.imageshack.us/my.php?image=screenex2.jpg)

---

### Post by computergeek6 on 2008-06-23
Why isn't the live-cd option there?

---

### Post by computergeek6 on 2008-08-07
Please help me figure out why this isn't working. It's driving me crazy!

---

### Post by cyberdork33 on 2008-08-07
> **computergeek6 said:**
> Please help me figure out why this isn't working. It's driving me crazy!
That is the menu from the alternate installer cd. You want to get the normal desktop livecd...

---

### Post by mikjp on 2008-08-09
> **computergeek6 said:**
> I have one of the Intel iMacs, and I want to install Ubuntu on it. The problem is that I need to be REALLY sure that my data is safe.

In that case, you should backup your data.

mikko

---

### Post by issih on 2008-08-09
There is no way to guarantee data safety short of backing things up.. Unless you have lots of videos you can probably back up your personal data on a few dvds, and its probably worth doing. I'd give you odds of 90% or better of things going fine, but the simple fact is that when messing with things at the OS/Partitioning level you can wipe out your drives either through user error or software/hardware failure.

There is no way to guarantee that it'll all be fine, just as we can't guarantee your hard drive won't blow up tomorrow, it does happen, you just have to hope you aren't unlucky.

As for the rest of it, use refit, it makes life easier, if you don' want to keep it once you've sorted out the partition table error, uninstall it, you can then just hold alt to select the OS at boot as is normal on an apple.

You don't need to worry about using the 64 bit or 32 bit system too much. For the easiest life I'd say use the 32 bit editions, they are slightly less buggy on average, and more software is ready for them, either will work on your hardware, thats the point of processors like the coreduo/2duo and athlon64s.

It also doesn't really matter if you use the live cd or the alternate cd (which is intended for installing on computers that have issues with the live cd), its just a way of installing the system, the live cd is probably friendlier for a new user, but thats about it.

Follow the guides, use bootcamp to partition your setup, install ubuntu, use refit to fix the partition table, and use the system, its not too bad once you stop worrying about it.

The best thing you can do to put your mind at rest is to back up your data..that way you can always just wipe the whole thing and reinstall leopard, at that point you  can play with impunity.

Hope that helps

---

### Post by ZachS on 2008-08-09
I do the same thing, and let me just recommend something to you, get refit, it is a very cool dual-booter. Just saying, once you get everything working, download refit through your mac.

---

### Post by computergeek6 on 2008-11-19
I have the system installed and booting, but when I load Ubuntu, the screen seems like each line of pixels is offset from itself. It looks like this:

XXX________XXX
________XXX________XXX
XXX________XXX
________XXX________XXX
XXX________XXX
________XXX________XXX
XXX________XXX
________XXX________XXX
___XXX    XXX
________XXXXXXXX
"X" = On Pixel
"_" = Off Pixel

Does anyone know what's wrong?

EDIT: Never mind. I had to install the proprietary video drivers

---

### Post by computergeek6 on 2008-11-19
How do I get Compiz Fusion working?

---

### Post by galexcd on 2008-11-20
> **computergeek6 said:**
> How do I get Compiz Fusion working?

There are plenty of tutorials online that can help you install it via the terminal, but I just used synapic to install it.

---

### Post by computergeek6 on 2008-11-24
I have it installed, but it doesn't do anything once I start it, then if I close it, it makes the system go crazy.

---

