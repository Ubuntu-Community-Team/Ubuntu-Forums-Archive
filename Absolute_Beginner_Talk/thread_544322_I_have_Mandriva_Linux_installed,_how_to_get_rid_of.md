---
title: "I have Mandriva Linux installed, how to get rid of it?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by siriusbg on 2007-09-06
Hello :)

I am new to the Li world, although I have a Mandriva 2005 Linux installed since 2005. I ruined it, because I really didn't know what I was doing - the graphical environment got LOST, there was no possibility to configure the internet etc. etc.

Despite this unfortunate progress I was determined to have a working Linux.  Then I understood aobut ubuntu. I downloaded the liveCD and I REALLY liked it. But the thing that stops me getting ubuntu installed, is my ignorance. There are some things that worry me : 
1. Take a look at this scrshot - [http://xs.to/xs.php?h=xs319&d=07364&f=Screenshot-308.jpg](http://xs.to/xs.php?h=xs319&d=07364&f=Screenshot-308.jpg). These are my HDD, and on the ext3 I have this Mandriva installed. How to remove Mandriva and install Ubuntu? The most logical solution would be to remove the ext3 partitions, but I fear that smth might get wrong and  ruin the Windows.

2. As it can be easily seen, I have a WinXP. Together with the Mandriva, they exist in my bootloader - I think it is LiLo, but I am not sure and I don't know how to check it. If I manage to remove Mandriva it would  affect in some way the boootloader and the proper loading of the XP?

p.s. A friend told me that the use of Partition Magic requires reinstallation of Windows - something that I've never done before. Is it true?

---

### Post by armandh on 2007-09-06
the only thing I have found to get the boot loaders out is a win 98 start up disk. and at the A prompt

fdisk /mbr    [but a new install will likely overwrite the mbr]

otherwise I like this   [http://partedmagic.com/](http://partedmagic.com/) its graphic display leaves little room for error.

always back up B4 major changes but were it mine, I would wipe the Mandrivia partition, leaving it unasigned 
then pick the "use unasigned space" option in the Ubuntu setup partitioning options

---

### Post by n3tfury on 2007-09-06
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

personally, i used  [gparted]("http://gparted.sourceforge.net/") for partitioning, but it works for most people using the built in partitioner.

---

### Post by henriette_holm on 2007-09-06
I'm quite sure you should be able to install Ubuntu, remove Mandriva and keep you Windows installation in one piece. You want to do the following things:

1) BACKUP BACKUP BACKUP - do a backup of all your important files and make sure that the backup is ok.

2) Boot the Ubuntu cd

3) Follow the installation instructions. When asked about partitioning choose manual - or something like that. If the current 10 Gb ext3 partition is your current / in Mandriva map it as the / of Ubuntu - similar with the rest of the ext3 partitions.

4) Follow the rest of the instructions and everything should be fine.

You'll be able to find fore information here:

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

The only thing that has me a bit worried is the fact that you have the partitions on an extended partition together with one of the windows partitions. But I think you should be ok.

Grub should overwrite the lilo boot loader and find your windows installation.

Don't use partition magic - there's no need. And no, it's no true

/Henriette

---

### Post by siriusbg on 2007-09-06
I am very, VERY thankful to  **henriette_holm**, **n3tfury and armandh** for the help. With this info, thoroughly depicted in screenshots, I guess I shouldn't have any serious problems..

---

### Post by hyper_ch on 2007-09-06
lilo shouldn't pose any problem... and you can use, upon install, the existing ext3/swap partitions if you like their sizes... to use those, just select manual partitioning :)
After that grub should install itself (or at least you should be asked if you want to overwrite the existing lilo).

---

