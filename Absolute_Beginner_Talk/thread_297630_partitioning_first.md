---
title: "partitioning first?"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-11-11
im getting a computer and i want to install xubuntu on it, i think i read some where that it has a partitioner on the disk.  because i want to keep windows.  or do i have partition it first

---

### Post by bigken on 2006-11-11
the installer has a partitioner  but  yhou can also do this with gparted liveCD ;)

its in my signature if you want to download it

---

### Post by lordvolo on 2006-11-11
okay thanks

---

### Post by Average Joe on 2006-11-11
If you are planning to install both Windows and Ubuntu from scratch, I would advise you to first install Windows, and then resize the partition and install Ubuntu. When you first install Ubuntu, Windows might overwrite it when you install it, because Windows usually doesn't like to share a hard disk with another operating system.

---

### Post by noranthon on 2006-11-14
I just tried the Xubuntu 6.10 installer (text method - I don't know what the OEM means).  I am using the "alternate" disk.

We got stuck at the so-called partitioner.  I have partition sda7 ready and waiting, except that it needs to be given a mount point.  This benighted installer only recognises the entire disk as a partition and the only option I get to proceed is to wipe the partition table.  No thanks.

Have I missed something?  Is it possible to install Xubuntu on sda7?  If so, how?

---

### Post by ReaderRat on 2006-11-14
> **lordvolo said:**
> im getting a computer and i want to install xubuntu on it, i think i read some where that it has a partitioner on the disk.  because i want to keep windows.  or do i have partition it first
If you are doing a fresh install, you need to remove **all** partitions and start from scratch. 
1 -As has been said, Install Windoze first, so it will not overwrite GRUB (your opening menu).
2 - Use the partitioner to resize your Windoze partition (so there will be a space for the Ubuntu partitions).
3 - Let the installer install Ubuntu to the open space on the drive.
4 - See these:
[**Resize Partition**](http://www.ubuntuforums.org/showpost.php?p=1642649&postcount=2)
[**Partitioning (XP & Ubuntu)**](http://psychocats.net/ubuntu/partitioning)
[**Installing Ubuntu**](http://www.psychocats.net/ubuntu/installing)

---

### Post by dwblas on 2006-11-14
The mount point is / if that is where you want to install to.  Ubuntu will install to and boot from the partition that is mounted on / (if you are booting to Ubuntu and not Windows of course).  So you want to make / the mount point and format the partition that you will be using for Ubuntu.  It will also format the swap partition.  I suggest you uncheck any other partitions that it may want to format - i.e. uncheck the format box in the install.  If you have other partitions,  Ubuntu will automatically mount them in /media.  You can change this in the /etc/fstab file.

---

### Post by Bartender on 2006-11-14
It sounds to me like we need to see a picture.  Can you download [GParted]("http://gparted.sourceforge.net/livecd.php") and burn to a CD?  This makes a bootable CD that will start up before Windows does, just like the Ubuntu install CD's.  If you can spin up GParted and take a screen shot or even a digital picture of the partition map that GParted will display, then plug that into a post, we can see what's going on.
If you have just Windows on your HDD, I don't understand how you got all the way to sda7 already.

---

### Post by noranthon on 2006-11-14
Hi, bartender.  I think you are replying to me.  Since posting to this thread I found another 2 or 3 threads more on point.  The Xbuntu alternate installer just does not work; it will not recognise existing partitions.

sda1: Mandriva 2006 (getting out of date)
sda3: Mandriva 2007 (released before its ready)
sda4: Sabayon (gentoo-based - I haven't got time yet)
sda5: swap
sda6: /shared (data files,etc)
sda7: intended for Xubuntu (which I can't install)

---

