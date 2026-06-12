---
title: "Hardware trouble"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-03-25
](*,) well, having  great day so far,
was getting started on assignment when computer shutdown instantly and wouldn't restart
so went to get second hand power supply from shop up the road. still wouldn't powerup. must be motherboard >?
so flatmate says, I can look at her computer to see if windows is running. I whack my hard drive in so I can continue with my work and bang, that computer won't start either . The main fan and cpu fan spin for under a second and thats it. so it was working fine before I tried to use my hard drive. Obviously have tried all troubleshooting at hand to find the problem but have narrowed it down to motherboard / cpu. any one have any idea what the problem is or what I have done?
 (need help)

---

### Post by Pragmatist on 2006-03-25
Just a silly question: Did you check that the wires from the power button where connected correctly?

---

### Post by carverj on 2006-03-25
Thanks pragmatist. :-D 
You managed to isolate and fix the problem straight off the bat.
I decided to daisy chain the hard drive from the original as a secondary slave drive so that I may attempt to access my home partition and I know it's there but cannot boot to it or access it as yet. Is there a way that you know of?
cheers in advance

____________
If more of us valued food and cheer and song above hoarded gold, it would be a merrier world. - J.R.R Tolkien

---

### Post by Pragmatist on 2006-03-25
> Originally Posted by: **carverj**
I* decided to daisy chain the hard drive from the original as a secondary slave drive so that I may attempt to access my home partition and I know it's there but cannot boot to it or access it as yet. Is there a way that you know of?cheers in advance*

What do you mean by daisy chain?  What kind of hard drives do you have?(IDE? SCSI? SATA?)   How many drives?  What Operating Systems (OSes) are you using?  Which OSes are on which drives?  Can you boot to any OS now?  What recent changes have you made?

---

### Post by carverj on 2006-03-26
yup sure, I took the hard drive from the recently deceased computer ( IDE 20 G with Ubuntu and win2000 dual boot), removed jumper to make it slave to a 40 G IDE hard drive. Then I installed XP on the primary 40 G IDE and can see the 3 partitions of the slave in computer management. So my question is, if I know the two hard drives are connected to the same IDE cable, is there a way I can access the data on the slave?
_______________
Hardware /nm./: the part of the computer that you can kick.

---

### Post by Pragmatist on 2006-03-26
> Originally Posted by: **carverj**
I whack my hard drive in so I can continue with my work and bang, that computer won't start either . The main fan and cpu fan spin for under a second and thats it. so it was working fine before I tried to use my hard drive. Obviously have tried all troubleshooting at hand to find the problem but have narrowed it down to motherboard / cpu. any one have any idea what the problem is or what I have done.....So my question is, if I know the two hard drives are connected to the same IDE cable, is there a way I can access the data on the slave?

So your original problem is no longer?

I don't think the fact that the drives are on the same IDE has anything to do with their accessability to one another.

I'm pretty sure that you can read and write to NTFS drives (your winXP and win2000) if you use SAMBA.  However, in this case both systems are running, so you can't do this with your setup.  You can read from the NTFS by mounting the partition.  See this wiki:
[https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28mount%29](https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28mount%29)

If you want to look through the ubuntu wiki you'll find some stuff on software to write to NTFS drives, however they state that this is experminental (read: risky).

The solution most people opt for, to network between drives/OSes within the same computer, is to create a FAT32 partition where all joint information is read and written to.  Both Linux and Windows can read and write to FAT32, so this is a 'shared partition'.

---

### Post by carverj on 2006-03-27
Just want to run over an idea my classmate and I had in this situation. Please feel free to comment/add everyone...

Will firstly change jumpers to boot into original hard drive (20G - 5G ubuntu, 10 G win2000, 5G /home ext3 and swap) in order to burn dvd containing my personal data (hda6 -ext3). then as you say, create shared FAT 32 filesystem by formatting entire (original ) drive and installing windows. So in summary, (once jumper removed to make slave) secondary 20G hard drive with single 20G win2000 FAT 32 on same IDE cable as new 40G drive currently running XP. Will install Ubuntu in 15G partition and take it from there (ie, research ways to access/backup to slave FAT32 drive)

Hope this makes sense as am quite new
____________________
Always tell the truth. That way, you don't have to remember what you said. 
-- Mark Twain

---

### Post by lord sooty on 2006-03-27
I don't know if this will help but you can get a windows box to read linux partions with this driver.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Pragmatist on 2006-03-27
> Originally Posted by: **carverj**
Will firstly change jumpers to boot into original hard drive (20G - 5G ubuntu, 10 G win2000, 5G /home ext3 and swap) in order to burn dvd containing my personal data (hda6 -ext3). then as you say, create shared FAT 32 filesystem by formatting entire (original ) drive and installing windows. So in summary, (once jumper removed to make slave) secondary 20G hard drive with single 20G win2000 FAT 32 on same IDE cable as new 40G drive currently running XP. Will install Ubuntu in 15G partition and take it from there (ie, research ways to access/backup to slave FAT32 drive) 
1.) Backup Data: You can switch the boot order in your BIOS which is much easier than changing jumpers back and forth.

2.) Create FAT32 partition: You don't need to install windows to get a FAT32 partition. FAT32, NTFS, ext3, ext2, are filesystem types. You probably could do it the way your describing, but your giving up using NTFS with Win2000. NTFS is an improvement on FAT32 and so its use is highly recommended by microsoft. What I was suggesting, is you can take this second drive, install win2000 with ntfs, use QT_Parted tool to resize the win2000 partition and free up space. Now you have 10GB /dev/hdb1 partition with win2000 on it and 10GB on unpartitioned space. Now you divide that 10 GB remaining space into several partitions for linux and finally, you install Ubuntu and when it comes to the partition page, make your choice based on what you already decided when partitioning with QTParted:

So you end up with something like this:[SIZE=1]
   [/SIZE]
```
partition       filesystem      partition       mount
type            type            name            point
-------------------------------------------------------
primary         NTFS            /dev/hdb1
primary         FAT32           /dev/hdb2
primary         swap            /dev/hdb3
logical         ext3            /dev/hdb5       /
logical         ext3            /dev/hdb6       /home

```

---

### Post by carverj on 2006-06-06
```
partition       filesystem      partition       mount
type            type            name            point
-------------------------------------------------------
primary         NTFS            /dev/hdb1
primary         FAT32           /dev/hdb2
primary         swap            /dev/hdb3
logical         ext3            /dev/hdb5       /
logical         ext3            /dev/hdb6       /home
```

What is the fat32 partition used for?
do you need just the one swap partition per disk or would it be wise to add a second swap for linux at the end of the disk. I assume the swap above /dev/hdb3 is windows as it has the type 'primary'. 
Also, at this stage I have :

```
partition       filesystem      partition       mount
type            type            name            point
-------------------------------------------------------
?                 vfat            /dev/hdb1


?                 ext3            /dev/hdb5       /
?                 ext3            /dev/hdb6       /home
```

and even though it doesn't show through Gnome System Monitor, there is swap at the end of the slave disk
I take it vfat just means fat32?
The reason I used fat was that I heard through forum that it had to be fat in order for Ubuntu to read and write to it !?!

Sorry for the late reply.... learning java  :)

---

### Post by Pragmatist on 2006-06-06
>  Originally Posted by: **carverj** 
  	Code:
 	[LEFT]partition       filesystem      partition       mount
type            type            name            point
-------------------------------------------------------
primary         NTFS            /dev/hdb1
primary         FAT32           /dev/hdb2
primary         swap            /dev/hdb3
logical         ext3            /dev/hdb5       /
logical         ext3            /dev/hdb6       /home[/LEFT]
 
   
  What is the **fat32** partition used for?
 
 >  Originally Posted by: **Pragmatist**
  The **solution** most people opt for, to network between drives/OSes within the same computer, is to create a **FAT32 **partition where all joint information is read and written to. Both Linux and Windows can read and write to **FAT32**, so this is a '**shared partition**'.
 
 > Originally Posted by: **carverj** 
 do you need just the one swap partition per disk or would it be wise to add a second swap for linux at the end of the disk. I assume the swap above /dev/hdb3 is windows as it has the type 'primary'.
 
 **Linux needs only one swap partition**.   A swap partition is, in Windows terminology, "virtual memory".  It is hard disk space used as if it were RAM.  RAM is much faster than the hard disk, but it is also much smaller.  Sometimes it is helpful to have more space to use as RAM, even if it is on the hard drive.
 
 The term **primary **is not specific to Windows.  It comes from the olden days of the DOS Operating System.  Back then the system was designed with only 4 partitions.  Then, when this original system was clearly insufficient, they 'extended' it by allowing any primary partition to become an extended partition.  An extended partition can have a large number of 'logical' partitions.  Why didn't they just make a whole new system?  Who knows!
 
 The reason you are associating Windows and Primary partitions is because **it is often necessary to put Windows on the first primary partition** (Windows is often inflexible).
 
 **Windows doesn't use 'swap' partitions**.
 
 > Originally Posted by: [B]carverj
[/B] I take it vfat just means fat32?
 The reason I used fat was that I heard through forum that it had to be fat in order for Ubuntu to read and write to it !?!
 
 vfat is a filesystem that Linux uses to read Windows' FAT filesystem.  vfat is a better filesystem than FAT (Remember, even Windows replaced FAT with NTFS).  However, basically you are right: for practical purposes, vfat just means fat32.
 
 Read my earlier posts (including my quote in this post) to understand more about what Linux and Windows require to communicate with each other.

---

### Post by carverj on 2006-06-13
[/CODE]> Windows doesn't use 'swap' partitions.


So does this mean that windows just uses a virtual location within the 
same primary partition  as virtual memory as opposed to Linux using a 
partition usually at the end to the drive?

Thanks very much pragmatist. The link you originally posted gave me the information I needed to edit fstab allowing the two windows partitions to be mounted upon startup. As follows:
[CODE]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hdb1       /media/hdb1     vfat    iocharset=utf8,umask=000,shortname=mixed,uid=1000,gid=1000        0       0
/dev/hdb5       /media/hdb5     ext3    defaults        0       2
/dev/hdb6       /media/hdb6     ext3    defaults        0       2
/dev/hda8       none            swap    sw              0       0
/dev/hdb7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

