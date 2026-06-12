---
title: "How to use Partition Magic to ready hard disk?"
date: 2005-06-19
forum: Absolute Beginner Talk
---

### Post by CoriolisSTORM on 2005-06-19
Okay everyone, I just went out and broke down and bought Partition Magic 8.0.  What do I need to do with it to enable me to install Ubuntu with no problems?  Do I also need to install the Boot Magic program as well?  Detailed instructions will be greatly appreciated.  Thanks!

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=CoriolisSTORM]Okay everyone, I just went out and broke down and bought Partition Magic 8.0.  What do I need to do with it to enable me to install Ubuntu with no problems?  Do I also need to install the Boot Magic program as well?  Detailed instructions will be greatly appreciated.  Thanks![/QUOTE]


First, defrag you ntfs drive. Then use partition magic to cut off some of the free space of the ntfs drive (at least 5 gigs I would say) and have that be unpartitioned free space for Ubuntu to install on. Boot from the Ubuntu install CD, and go with the defaults till it get to the "guided partitioning part." Then tell it "no" when it asks to make changes to disks. 

Here, say no here:

[http://shots.osdir.com/slideshows/slideshow.php?release=152&slide=15](http://shots.osdir.com/slideshows/slideshow.php?release=152&slide=15)

This will send you to the partitioner.

Use the arrow keys to select the unpartitioned free space. Hit enter. 

Wait I need to know something...how much RAM do you have?

---

### Post by CoriolisSTORM on 2005-06-19
I have 512 MBs however, I have an onboard Geforce 4 MX(junk) that cuts into that.  I think I need a swap partition as well.
EDIT:  I have it set up correctly now and Ubuntu installed!  Yes!  Now, how do I get a piece of crap winmodem working in it?  It is an Agere Win Modem.  It is in PCI slot 3.  While I'm thinking about, it also, how do I get Ubuntu to read (not write, heaven forbid) my NTFS partition?

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=CoriolisSTORM] While I'm thinking about, it also, how do I get Ubuntu to read (not write, heaven forbid) my NTFS partition?[/QUOTE]


[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by geearf on 2005-06-23
Hello,

just to let you know of something : 

From the day i started using Ubuntu to yesterday, everytime i needed some room for linux, i just booted in windows, resize the ntfs partition with PM, and give the space to any linux partition.

Yesterday i decided to transform my fat32 partition (for exchange between both os) to an ext3, all went good, except that when i wanted to give more room to my /home (which is my last partition), it killed my /, so now i have to reinstall ubuntu again :(

I'm glad i have more than one partition so i still have my files, but still i guess i won't ever try anything with PM anymore after installing it again :(

---

### Post by jsimmons on 2005-06-23
[QUOTE=geearf]Hello,

just to let you know of something : 

From the day i started using Ubuntu to yesterday, everytime i needed some room for linux, i just booted in windows, resize the ntfs partition with PM, and give the space to any linux partition.

Yesterday i decided to transform my fat32 partition (for exchange between both os) to an ext3, all went good, except that when i wanted to give more room to my /home (which is my last partition), it killed my /, so now i have to reinstall ubuntu again :(

I'm glad i have more than one partition so i still have my files, but still i guess i won't ever try anything with PM anymore after installing it again :([/QUOTE]
 I've halfway decided to buy another drive and put linux on it instead of putzing around with my Windows boot drive.

---

### Post by geearf on 2005-06-23
Well, my partitions list was / is like this : 

NTFS
FAT32 / ext3
/
swap
/home


When i resized the NTFS and the FAT32 i had no problem at all, the problem came when i wanted to transport the space to the /home, as it needs to move the other partitions ... Don't really know what happened, but now i only have 3M of files on my / :cry:

---

### Post by crashtest on 2005-06-23
[QUOTE=jsimmons]I've halfway decided to buy another drive and put linux on it instead of putzing around with my Windows boot drive.[/QUOTE]

Whenever I make a dual boot machine, I use Partition Magic to make a fat32 partiton that can be mounted by both the Windows and Linux systems.  Usually something around 5 Gb in size.  Unlike NTFS, Linux has NO problems reading and writing on FAT32.

On Windows this will be seen as the "e" drive, or f, g, or whatever, depending on how many drives are in the computer.

On the Linux side I make a directory "/shared" - call it whatever you like.  Add an entry in /etc/fstab like "/dev/hda5       /shared     vfat    user,umask=000,rw     0 0"
(Again the partition may be something other than /dev/hda5 on your system.  You can see what it is during the Ubuntu install.)

Now whatever files you think may be needed in both Windows and Linux can be kept in the shared partition, and can be used read/write by both operating systems.  Hope this helps.

---

### Post by jsimmons on 2005-06-23
[QUOTE=crashtest]Whenever I make a dual boot machine, I use Partition Magic to make a fat32 partiton that can be mounted by both the Windows and Linux systems.  Usually something around 5 Gb in size.  Unlike NTFS, Linux has NO problems reading and writing on FAT32.

On Windows this will be seen as the "e" drive, or f, g, or whatever, depending on how many drives are in the computer.

On the Linux side I make a directory "/shared" - call it whatever you like.  Add an entry in /etc/fstab like "/dev/hda5       /shared     vfat    user,umask=000,rw     0 0"
(Again the partition may be something other than /dev/hda5 on your system.  You can see what it is during the Ubuntu install.)

Now whatever files you think may be needed in both Windows and Linux can be kept in the shared partition, and can be used read/write by both operating systems.  Hope this helps.[/QUOTE]
 I current have three hard drives in my system.  Two 80gb IDE drives, and a 160gb SATA drive.    My Windows boot drive (NTFS format) is 80gb in size for no reason other than the drive only cost me $24 new (after rebates).  The other two drives (the other 80gb IDE and the 160GB SATA) are partitioned into drives D through K.  All of those partitions are FAT32.

Since I have an open SATA port, I am seriously considering just buying another SATA drive (probably another 160gb) and installing linux (Ubuntu) onto that drive allowing me to dual boot without messing with my existing Windows partitions at all.  I don't relish the thought of a minor partition change hiccup forcing me to reinstall Windows, and it's worth $100 to me to avoid the potential problems.

---

### Post by geearf on 2005-06-23
i miss the old days when i had 2 hard drives, and more than 80G :)

---

