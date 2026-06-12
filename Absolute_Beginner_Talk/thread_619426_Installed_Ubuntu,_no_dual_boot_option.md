---
title: "Installed Ubuntu, no dual boot option"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by AND_YOU_ARE on 2007-11-21
I installed Ubuntu on one of the four hard drives in my case.  I wiped a 160GB drive clean, and reformatted it in windows.  I then proceded to disconnect the other three drives, and boot with the Ubuntu disc in my DVD drive.  The install went quickly on my C2D.  I did not have any problems until I connected all the hard drives back together and booted my pc.  The system booted directly into my WinXP install.  The only way I boot into Ubuntu is to chage the boot drive in the bios, or remove WinXP HDD.

My question remains, should I have installed Ubuntu on the fourth drive I set aside for it with all the other drives attached?  Should I wipe my fourth drive, and start the install process over with every drive hooked up?  I am looking for the ability to dual boot with the menu option to choose which OS to boot from.

---

### Post by TidusBlade on 2007-11-21
I would recommend trying it with all drives connected, I relized a part in the installation where it detects the hardware so it could be useful if it detects those 3 other drives.

---

### Post by qamelian on 2007-11-21
Since you had the other drives detached, the Ubuntu installer would have no way of knowing that there were other OSs involved. You're going to need to edit /boot/grub/menu.lst by had now to set up the other OSs. Personally, I prefer to just leave all my drives installed and let Ubuntu do the work.

---

### Post by AND_YOU_ARE on 2007-11-21
Sounds good.  I'll give it a try this evening.

The one thing I noticed when I booted into windows, was that the fourth hard drive does not show up in windows explorer, but it doest appear in computer management with the other drives and patitions.  

Would it be a good idea to have the Ubunut drive be shown in windows, and would it be a good idea to move files from one of the other three drives to the ubuntu drive while booted into windows?  Or is this a bad idea?

---

### Post by Bigbird999 on 2007-11-21
I'm a Linux newb and I'm pretty sure I know what you want.  It took me a while to put all the pieces together but I finally was able to do what I wanted by installing Ubuntu onto the same hard drive as windows, and letting the install disk resize the windows partition to make room for Ubuntu and swap partitions, I followed a 'dual boot' how to found on the forum. So if I were you, I would connect all my drives, Boot from the CD, choose Manual in the partition screen and size your partitions. on the 160 GB drives 

I would recommend say 15 GB for Windows OS and programs,  10 GB for Linux, A swap = 2x installed RAM, a separate /home partition  of say 80GB and a separate 60 GB partiton for windows data, unless you want to keep all of your windows data on the same drive as the OS.  The tutorial I followed sugested formating the windows data partition  as FAT32 so both windows and Ubuntu can see it and write to it, so that is what I did.  Later I discovered that there is software available that allows windows to see Linux ext formatted disks and Linux to see windows NFTS formatted disks. So this is not really necessary, but it is easy.  

The main thing is to defrag your 160 GB drive first so that all the data is together and there is enough contigious empty space for the Linux partitions to install.  And make sure that you choose manual install otherwise it will destroy your 160 GB windows partiton and install Linux on it.  

Partitioning processes can, and sometimes, do, screw up,  So make sure you back up your data from the windows drive before you do the install.  For me it worked perfectly first time.

The reason Windows doesn't see the 4th hard drive where you installed Linux is that you don't have the software that allows window to see the ext 2 and ext3 formatted partitions.

The reason I use a small partition for the OS is that I can reformat or restore an image of a working system without losing any data.  

In my case I have a crappy old laptop with 4 partitions 
6 GB for Win2Kpro
4 GB for Gutsy
1GB Linux swap
9 GB Data share formatted as FAT32 both OSs store their data here

When I boot, I am given a screen that les me choose my OS

Pretty sure that is what you want  Hope it helps you.

EDIT:  Here is one tutorial  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

BB

---

### Post by AND_YOU_ARE on 2007-11-21
I have a 320GB drive for my windows OS, and I dont want to have the Ubuntu install on this hard drive.  My plan was to use the 160GB drive for only the Ubuntu install.  I would prefer not to change the windows os file format from NTFS to FAT32, so I can live without the ability to write to the other OS's drive.

With my two other drives (320GB and 500GB) both on NTFS are used for my file storage, can Ubuntu write to these?  Or should I splt up the 160 into two 80GB and have one of the 80GB has a partition that can be written by both?

---

