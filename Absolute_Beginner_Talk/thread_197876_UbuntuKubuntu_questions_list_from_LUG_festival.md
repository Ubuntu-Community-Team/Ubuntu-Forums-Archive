---
title: "Ubuntu/Kubuntu questions list from LUG festival"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by arunpawar on 2006-06-16
Here is list of questions i have collected when i attended the linux user group in our university campus.The discussions was on ubuntu and some programming stuff.Some questions may sound vague but may be many of us can learn from it?
I've passed some questions here,Hope that you guys will help me get answer.

1. Which filesystem is used in ubuntu,kubuntu? i.e xfs or ext2/3 etc.
2. Which linux kernel is used in ubuntu,kubuntu? i.e debian or is derived from other distribution?
3. Why to mount floppy & cdrom when just plug n play will do the job?
4. What directories are vailable in kubuntu,i.e /var or /mount what role they play in kubuntu?
5. What commands are avalaible for formatting & partitions,also any utility available to partition?
6. Where can i find the dual boot (Win+ubuntu) installation guide for ubuntu/kubuntu?
7. Why debian is different than other distro kernels like Redhat,mandriva ?In what way?
8. Why some good features in ubuntu are not available in kubuntu like add/remove application tool that is avalaible in ubuntu only?
9.  How can i install the software from source i.e using TARballs?
10. is it possible to update my current kubuntu to version 6.06 with help of shipit cd?
11. Is it possible to burn cd using kubuntu,if the kubuntu is installed under VMware workstation?
12. How can i install the window decorations,themes from kde-look.org to my kubuntu desktop?
13. Why kubuntu don't have its own window decoration,theme ?as ubuntu have own Human theme already. 
14. How to create a window decorations or theme for kde?
15.What is the repository thing?Is it possible to install application from magazine cd or debian cds into kubuntu?How?

Most tricky question: In what way ubuntu is diffrent than kubuntu?Which flavour needs more support of users?

You can answer me i question/answer format if you want to,thanks in advance.Hope you will help.:eek:

---

### Post by aysiu on 2006-06-16
Those are a lot of questions. Anyone else mind if I take a first stab at it, so we don't have a million of the same replies? Other people can fill in the blanks later. [quote=arunpawar]1. Which filesystem is used in ubuntu,kubuntu? i.e xfs or ext2/3 etc.[/quote] Ubuntu defaults to Ext3.
> 2. Which linux kernel is used in ubuntu,kubuntu? i.e debian or is derived from other distribution? Ubuntu is Debian-based, but I think all distributions use the same kernel. Can someone confirm or deny this? > 3. Why to mount floppy & cdrom when just plug n play will do the job? Floppies can be tricky (mine automounts fine, but I know others have had problems). CD-ROMs should just plug-and-play. > 4. What directories are vailable in kubuntu,i.e /var or /mount what role they play in kubuntu? All directories are valuable--otherwise, they wouldn't be there! > 5. What commands are avalaible for formatting & partitions,also any utility available to partition? I don't know the commands, but you can use GParted or QTParted, which are graphical partitioning applications. GParted comes with the Ubuntu Desktop CD. > 6. Where can i find the dual boot (Win+ubuntu) installation guide for ubuntu/kubuntu? [http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html) or [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) > 7. Why debian is different than other distro kernels like Redhat,mandriva ?In what way? It's not that different. They just different package management, have different release cycles, different organizational structures, and different goals. > 8. Why some good features in ubuntu are not available in kubuntu like add/remove application tool that is avalaible in ubuntu only? The Add/Remove application tool is available for both Kubuntu and Ubuntu. Ubuntu defaults to using a package manager frontend called Synaptic Package Manager. Kubuntu defaults to using a package manager frontend called Adept Package Manager. You can use Adept in Ubuntu if you want. You can also use Synaptic in Kubuntu if you want. > 9. How can i install the software from source i.e using TARballs? Read this: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) and this [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) > 10. is it possible to update my current kubuntu to version 6.06 with help of shipit cd? You can with the Alternate Install CD, not the Desktop CD. > 11. Is it possible to burn cd using kubuntu,if the kubuntu is installed under VMware workstation? That I don't know. > 12. How can i install the window decorations,themes from kde-look.org to my kubuntu desktop? You have to un-tar the theme and place it in the appropriate directory. If you're after easy theming, use Ubuntu instead of Kubuntu. > 13. Why kubuntu don't have its own window decoration,theme ?as ubuntu have own Human theme already. Kubuntu does have its own window decorations and themes. It defaults to using Lipstik, but it also Keramik and a few others installed. > 14. How to create a window decorations or theme for kde? Worry about that later. > 15.What is the repository thing?Is it possible to install application from magazine cd or debian cds into kubuntu?How? Read the aforementioned Psychocats and Monkeyblog links. > Most tricky question: In what way ubuntu is diffrent than kubuntu? They are the same distribution. Ubuntu has the Gnome desktop environment. Kubuntu has the KDE desktop environment.  Can we assume you already know the difference between Gnome and KDE? > Which flavour needs more support of users? Kubuntu. The support on these forums is unparalleled, but most of the users here use Ubuntu, not Kubuntu.

---

### Post by localzuk on 2006-06-16
[QUOTE=arunpawar]
1. Which filesystem is used in ubuntu,kubuntu? i.e xfs or ext2/3 etc.[/quote]

ext3 is standard but you can use many different ones (for example I use a mix of ext3, ext2 and reiserfs).

> 
2. Which linux kernel is used in ubuntu,kubuntu? i.e debian or is derived from other distribution?

It is the linux kernel... :) They all use the same one + patches. The distro was a branch from Debian...
> 
3. Why to mount floppy & cdrom when just plug n play will do the job?


What do you mean? Floppy drives do not actively scan for disks, so the mount has to be initiated by the computer (ie. a mount). CD rom drives are a permanent fixture in your computer, but you want to be able to change the discs in the drive. This means you need to be able to mount and unmount the discs in order to change them.

Plug and play (or hotplug) allows for new devices such as external usb keys to be added without too much hassle.

> 
4. What directories are vailable in kubuntu,i.e /var or /mount what role they play in kubuntu?


The same as any other standard linux distro. They all follow the same roles as other distros (the only difference I can see is /media is used for the mounting of drives).

> 
5. What commands are avalaible for formatting & partitions,also any utility available to partition?


gpartd is a graphical tool for partitioning. fdisk and cfdisk are command line programs. To format you would use something like mkreiserfs or similar depending on the partition type you wanted.

> 
6. Where can i find the dual boot (Win+ubuntu) installation guide for ubuntu/kubuntu?


I would say that you don't really need a guide. Instead take a look at the pointers here: [http://www.ubuntuforums.org/showthread.php?t=16287](http://www.ubuntuforums.org/showthread.php?t=16287)

Basically it comes down to:

1. Make sure you have some spare space on your hard disk
2. Make sure you have windows installed first
3. Install Ubuntu making use of the spare space on your disk
4. Install the Grub boot loader to the mbr of the primary boot disk

The rest is done for you.

> 
7. Why debian is different than other distro kernels like Redhat,mandriva ?In what way?


You probably want to ask the debian team that. But I would say it debian uses a very strict code of practice when it comes to the software that is included. It is not a business led distribution. It uses the .deb package system. It has a long release timetable.

> 
8. Why some good features in ubuntu are not available in kubuntu like add/remove application tool that is avalaible in ubuntu only?


This is due to Kubuntu being developed by the kubuntu developers and the main Ubuntu being developed by the Ubuntu team. There will likely always be differences. You can use the adept tool to do the job fine though. Also, there is an 'Add/Remove programs' entry in the K menu...

> 
9.  How can i install the software from source i.e using TARballs?


Take a look at [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

> 
10. is it possible to update my current kubuntu to version 6.06 with help of shipit cd?


Yes. If you have installed extra applications that aren't on the disc, then you will need an internet connection. Also, ensure that you have the metapackage 'kubuntu-desktop' installed before doing any updates.
You can either do an upgrade by booting from the disc, or preferably, by altering the /etc/apt/sources.list file to use 'dapper' instead of 'breezy'.

> 
11. Is it possible to burn cd using kubuntu,if the kubuntu is installed under VMware workstation?


It should be. VMWare has access to the cd drives, so I would think so. Although I haven't checked this.

> 
12. How can i install the window decorations,themes from kde-look.org to my kubuntu desktop?


Download one of them and read the INSTALL and README files for it. It usually involves compiling them.

> 
13. Why kubuntu don't have its own window decoration,theme ?as ubuntu have own Human theme already.


What do you mean? Kubuntu uses a blue theme consisting various already made components and its own colour scheme. It doesn't use the brown style of Ubuntu - just as Xubuntu uses purples IIRC.

>  
14. How to create a window decorations or theme for kde?


You are better asking that at the kde forums/kde-look forums as they will be able to provide you with more information.

> 
15.What is the repository thing?Is it possible to install application from magazine cd or debian cds into kubuntu?How?


The repositories are giant collections of software that are sat waiting to be installed. They are all specifically created to work with Ubuntu. You should only use ubuntu .debs or compile your own software for ubuntu really. If you install a debian package you may well have issues regarding package compatibility.

> 
Most tricky question: In what way ubuntu is diffrent than kubuntu?Which flavour needs more support of users?


Kubuntu is a desktop front end for the ubuntu system installable by installing the 'kubuntu-desktop' package, just as the official frontend is called 'ubuntu-desktop'. The difference is that kubuntu uses KDE and has tools that make use of the kde libraries and ubuntu uses the Gnome desktop and tools that make use of the gnome libraries. Both need support of as many users as they can.

Hope that lot helps

---

