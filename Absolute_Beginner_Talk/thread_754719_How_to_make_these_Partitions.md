---
title: "How to make these Partitions?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by thomas7.10 on 2008-04-14
Hi everyone!

Being a linux user now for quiet a time i'm still missing some things from the windows world. That's why i would like to have xp on my computer beside the common ubuntu. So right now i have ubuntu installed and it takes all the space on my harddrive.
I'm wondering now how i could make a port of about 100gb not formated and have another 100 gb as exchange space that both linux and windows can use.

Can anyone help me with that task?

Thomas

---

### Post by Michael.Godawski on 2008-04-14
Here is a guide how to install xp after ubuntu:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

You can use the Gparte Tool to create addtional partitions. FAT32 can be read by both operating systems.

---

### Post by rolnics on 2008-04-14
You need a program called gparted or there's a couple of other that the name I can't recall this early in the morning! You can either download the livecd of gparted or using the following menus you can install it in Ubuntu. 

Goto System -> administration -> Synaptic Program Manager. In Synaptic you can do a search and the check the program to install. I'm sure there's a command line option to install this, but I'm still learning! Once gparted is loaded up and scanned your disk(s) you can partition how you like.

---

### Post by Michael.Godawski on 2008-04-14
Here are some helpful guides on gparted:
[LIST]
[*][http://gparted.sourceforge.net/larry/livecd/main/livecd.htm](http://gparted.sourceforge.net/larry/livecd/main/livecd.htm)
[*][http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
[*][https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[/LIST]

**edit:** and always do a backup of your important files, when playing with partitioning.

---

### Post by Malta paul on 2008-04-14
Hi, There are quite a few way to partition your disk. Perhaps the simplest way if you are new to Ubuntu is to back up your Ubuntu personal files on a USB or CD then reinstall windows, this will zap Ubuntu. Then reinstall Ubuntu again from the live CD and use the default partition space as recommended for ubuntu.
Then you will be able to dual boot into either Windows or Ubuntu. 
Hope this helps:)

---

### Post by thomas7.10 on 2008-04-14
Now i'm thinking of following the tutorial [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) but can i access the linux files from the windows mashine?

---

### Post by angry_johnnie on 2008-04-14
> **thomas7.10 said:**
> Now i'm thinking of following the tutorial [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) but can i access the linux files from the windows mashine?

Windows cannot access ext3 filesystems by itself.
You would need something like [this]("http://www.fs-driver.org/") driver

---

### Post by Trail on 2008-04-14
> **Michael.Godawski said:**
> FAT32 can be read by both operating systems.

I'd just like to mention that NTFS can also be read by both systems. But is a bit slower (and I can say has issues with NTFS files on greek characters...)

---

### Post by thomas7.10 on 2008-04-14
As usual I run into some problems... 

I followed the tutorial and everything was working just fine until i came to the point of installing XP. The setup runs and is loading the drivers then i come to the point where it should display the partitions - but it doesn't show any partitions. Then on pressing any key i get a blue screen. 
I formated the unformated disk space to NTFS but that gave me the same result in the XP setup.

I hope someone could help me with that.

---

### Post by muteXe on 2008-04-14
I can't access that tutorial site from this machine (it's blocked by the corporate network for some reason), but i'd go with what "Malta Paul" posted to be honest.   Seems the most simplest/quickest/pain-free option.

mute

---

### Post by thomas7.10 on 2008-04-14
well now i would do so but i can't get the windows setup to work. I can't see any partition at all

---

