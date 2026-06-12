---
title: "Cannot install unbuntu on OS X Lion"
date: 2011-07-28
forum: Apple Hardware Users
---

### Post by MaxxABillion on 2011-07-28
I am beyond frustrated right now.  I really want to use ubuntu, however, I can't get it to install at all.  I've tried installing it in VMware, then I tried to run a dual boot via bootcamp.  The final error it has come down to was "unable to find a medium containing a live file system"    To clarify, I have a Macbook Pro 15"/2GHz Intel Core i7 / version 10.7 (OS X Lion)  I've tried EVERYTHING!!! Even using redit to boot from the live CD. I don't even get pass the command screen.  I'm starting to believe that this is a bug in Ubuntu 11.04 that causing problems with OS X Lion.  I've researched researched and researched to no avail.

---

### Post by mambeu on 2011-07-28
I think you're having the same problem I had, or at least you're seeing the same error message that I saw.

I was able to install Ubuntu by using the 11.10 daily build on both a DVD and a bootable USB stick.  See this post: [http://ubuntuforums.org/showpost.php?p=11006928&postcount=86]("http://ubuntuforums.org/showpost.php?p=11006928&postcount=86").

I have a MacBook Pro 8,1 (the newest generation 13-inch).  I was running Snow Leopard when I installed ubuntu, not sure if that makes a difference.

---

### Post by MaxxABillion on 2011-07-28
I tried that too man and I got the same problem.  I just wish someone running OS X Lion would step up and say if they've ran into the same problems or is it just me

---

### Post by duckwars on 2011-07-28
I don't know if this is exactly what you want to hear, but I just bought a 13" macbook air with lion and vmware fusion runs ubuntu flawlessly.

Well the only problem I have is getting the network to work when bridging it instead of using NAT...

I reallly wanna use synergy, but I need an ip address for the ubuntu.

---

### Post by Allsixcolours on 2011-07-29
I am currently running both Ubuntu 11.04 and Lion GM on a macbook pro 7,1, and had no troubles in installation. If you are using the final, market version of lion then there are likely some differences in the OS's inner workings, but I would generally assume you would have as little trouble installing as I did. 

I just burned a liveCD with 11.04 and hit alt directly after the "sound" at boot up with the disk already in, and booted from that. from there just make sure you pick the right partition to install to from the partition editor. Set mount point as "/", and be sure to install the grub on the same partition as where you are putting Ubuntu. I think I remember having some issue about "no recognizable file system" on my first install, and it was because I installed the grub in the wrong place. 

I'm not sure if its the same issue, but I figured I should let you know that (at least on my set up of lion and MBP)it is possible to install ubuntu on a system running lion. OS X is not going to recognize linux file systems, keep in mind, and the current OS on one partition should have NO EFFECT on a separate partition. Now, if you are trying to install over lion... I can't say it wont do something, but if you hit format while installing it should erase lion before it starts to install, eliminating any interaction between the two OS as well. 

Keep at it, you will probably figure it out yourself soon enough. I'm afraid I don't know much about linux, but I have a fair amount of knowledge of OS X and macbooks, so I hope I can help if you need more info.

Good luck!

---

### Post by BDNiner on 2011-07-29
I have a Mac Mini with Lion and was able to install Ubuntu 11.04 in Virtual box with no problems at all. It doesn't detect my AMD video card however. I have not attempted boot camp yet. I am waiting to fix the video card drivers issue before trying bootcamp.

---

### Post by Allsixcolours on 2011-07-29
Ah, one more thing. The first liveCD I made failed miserably and wasn't able to load anything beyond the blinking line on black screen. The second one I chose the lowest possible speed to burn with, after reading that this helped, and this second liveCD works wonders. I'd try to burn another disk. Also, Apple's bootloader boots the liveCD's just fine, you don't need another program to boot to the disk. Just hold alt and wait a few moments for the disk to load. So basically, try burning again at the lowest speed and see if it helps.

---

### Post by MaxxABillion on 2011-07-29
To see that you all have ubuntu installed and working is just demoralizing.  When I tired to install it on VMware two things happened.  My wifi stopped working and it gave me an error of "can't mount tools" or something like that.  So i went with trying to install via bootcamp.  I downloaded refit, I partitioned my hard drive, but as far as GRUB, I have no idea what that is, maybe that will help.

Any help that can be provided for both VMware or Bootcamp, i'll greatly appreciate it!!

---

### Post by Allsixcolours on 2011-07-29
the GRUB is the Ubuntu Bootloader, it is what starts up the OS. Without this, you cannot use Ubuntu. In the partition setup part of the installation, it asks for which partition to install on, and under that there is a drop down box that asks where the grub should be installed. be sure to pick the same partition from the list that you are installing ubuntu on.

As for boot camp, it is fairly simple. Just create a partition by sliding the slider over towards the OS X side until it is big enough for your needs and wants. REMEMBER THE SIZE. then continue following the instructions. When it asks about installing the windows support files, select that you have the support disk. It will then ask you to put in the disk and restart your computer. Theoretically it will automatically boot into the disk, but if it doesn't then restart and hold down the option (alt) key to bring up your bootable devices. After a moment the disk will come up, select it. Then follow the instructions of the Ubuntu Installer and you should be good. When it asks "Install with OS X, Install over OS X, and Other", choose other. then select the partition that is the same size as the partition you made (that is why you need to remember the size, so make it something easy to remember). Then look at the partition identifier, it will be Sda1, or something similar. Choose that identifier in the grub drop down list. Then the install starts and you should have no problems from there. 

I just went over the entire install process, and if that is not what you are having problems with then I'm going to feel like such a jerk :P From what I gather, your problems should be resolved with a good installation, and they were caused by some mistakes in the installation process. If it is indeed something else, then I apologize for blabbing on about all this. 

(Also, it helps if you install connected to an Ethernet cable, it should install the right drivers to use 3D graphics and Wifi automatically)

---

### Post by MaxxABillion on 2011-07-29
Allsixcolours, while your method is how it supposed to work, I never get to the install process.  Once I restart the computer and load form the CD, I get the purple ubuntu screen and then it stops at the command screen and says "unable to locate media containing live system file".  That's where I am now and after reading forums and researching there seems to be no definitive answer to get me past this point.

---

### Post by Allsixcolours on 2011-07-29
Ah. Well, that does make a bit of a difference. If you get the purple screen, the cd is properly made. Or at least I would assume. Have you tried pressing esc while on that screen? It'll take you to the menu where you can specify install, whereas by default it would take you to a liveCD session. It may be unable to run the live session for whatever reason, but the installer might work. Give it a try if you have not already. 

Thanks for clearing that up for me, I wasn't sure exactly what was going on.

---

### Post by MaxxABillion on 2011-07-31
yes I pressed escape also and nothing.  Its frustrating...

---

### Post by Scott Deagan on 2011-09-19
I had the same problem, I found that downloading the 'Mac' ISO from here:

[http://cdimage.ubuntu.com/releases/11.04/release/](http://cdimage.ubuntu.com/releases/11.04/release/)

solved the issue for me.

---

### Post by dpny on 2011-09-19
Haven't installed Ubuntu on bare hardware for a while, but 11.04 runs perfectly well in both Virtualbox and Parallels. Don't burn the .iso to a DVD. Simply add it to the virtual DVD drive in Virtualbox/Parallels and let it boot the .iso. Takes about 20 minutes to install.

---

### Post by ludwigbaum on 2011-11-29
Sorry, first version deleted.

---

### Post by ludwigbaum on 2011-11-29
There are several reasons for the problems described here.
1) Lion uses another partition-scheme than former systems. The difference is unvisible. You cannot repartition a lion-system by using the partitioning-tool of leopard. Why?
In the past, there was an unvisible LOGICAL partition, which separated the MacintoshHD-partition (OS-X) from the Bootcamp-partition. Consequently, you had the EFI-partition, the MacIntosh-partition and TWO other primary partitions at your disposition for Windows and a data-partition for Windows. 
Lion has changed that. The logical partition is now a PRIMARY partition, and there is only ONE primary partition left for Windows (Windows handles only four primary partitions). Triple-Booting OS-X, Windows and Linux will be difficult.
Attention: It is possible to kill that new primary partition after installing a simple, unconfigured Windows-system by using Partition-Wizard, for example. But Windows will no longer boot, because it is now on partition 3, while the boot-procedure searches it on partition 4. You can reinstall Windows. If you synchronize the partition-table with the Refit-Tool, Windows will be killed once again.

2) The new MacBooks delivered with Lion use a different firmware for booting. Linux-CDs, which boot everywhere else, will not boot. I tried Ubuntu, Mint, Fedora, OpenSuse (Gnome and KDE) on a MacBook-Pro 10/2011. I did not yet use DVD-media.

---

