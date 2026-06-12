---
title: "Can't view C: drive"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by glebreton on 2007-04-11
I have recently installed Ubuntu on a partition on my laptop on which I was running XP.
The dual boot works great!
However, I can't access my old c: drive. Is there any way I can change that now? 
I seem to be having some problems with wine because of this.
Thanks in advance,
Glebreton

---

### Post by taurus on 2007-04-11
You need to mount it before you can access it.  Have you mounted it?  Here is a guide on how to do that.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by ParkingBrake on 2007-04-11
This is from the official Ubuntu Desktop User Guide:

Make Windows partitions automatically available
Windows partitions should be automatically available from Ubuntu. If they are not, the following
procedure will make them automatically available:
First make a directory where the partition can be made available ("mounted"):
     sudo mkdir /media/windows
Next, back up your disk configuration file and open the file in a text editor with administrative
     privileges:
     sudo cp /etc/fstab /etc/fstab_backup
     sudo gedit /etc/fstab
Append the following line at the end of file:
     /dev/hda1 /media/windows ntfs umask=0222 0 0
               Replace /dev/hda1 with the correct device name for your partition.
               If your Windows partition uses the FAT32 filesystem, replace ntfs with vfat in the
               above command.
               If you have a FAT32 filesystem, it is also safe to allow read-write access. To do this,
               change the value of umask to 0000.
Save the edited file (an example [sample/fstab_automountntfs]).
The changes will take effect when the computer is restarted.

---

### Post by wormser on 2007-04-11
After learning to mount, if you need to write to the NTFS C: drive then check out this great post.
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by xsprayx313 on 2007-04-11
How do you get files from the C Drive? Say, I want to use my teamspeak on XP, or if i want to get a file on XP

---

### Post by taurus on 2007-04-11
You first need to mount your Windows partition before you can access it.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by arron on 2007-04-11
> **xsprayx313 said:**
> How do you get files from the C Drive? Say, I want to use my teamspeak on XP, or if i want to get a file on XP

There is a linux client for teamspeak that works quite well.  Remember Linux is a separate operating system, and you cant just copy programs over to run them.

You can install most windows programs via wine with minimal problems.  But most windows programs have a linux version, or some other program that does the same job.

Here is the linux teamspeak:
[http://www.goteamspeak.com/index.php?page=downloads](http://www.goteamspeak.com/index.php?page=downloads)

If your looking for other programs, post on here, and someone somewhere has found what will help you.

Welcome to the Ubuntu Community.

---

### Post by xsprayx313 on 2007-04-11
I did so and installed wine. I dont know what to do to run wine \ where to go.

---

### Post by tarek on 2007-04-11
Hi,

This is how you can see your c and other windows drivers:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

There are two file system types: NTFS and FAT

If you have FAT then you can view and modify the files, but with NTFS you can only see. There are ways to modify files under NTFS but still under testing.

tarek

---

### Post by taurus on 2007-04-11
Why do you have to run it through wine?  There is a linux version of it.  From the link above, click on Site 1 under Linux.  Scroll to the bottom to except the license agreement and download it, ts2_client_rc2_2032.tar.bz2.  After saving it to your machine, unpack it from a terminal with

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvjf ts2_client_rc2_2032.tar.bz2
cd ts2_client_rc2_2032
sudo ./setup.sh  <-- to install it
```

---

### Post by xsprayx313 on 2007-04-11
Yeah I already got linux TS, i was just giving an example. But it would be nice to just use the XP version of TS.

Going to read the link the person above you posted.

---

### Post by xsprayx313 on 2007-04-11
When trying to do so, i get /dev/hda1 does not exist

---

### Post by wormser on 2007-04-11
> **xsprayx313 said:**
> When trying to do so, i get /dev/hda1 does not exist

It could be named something else like sda1 on my laptop.

try:

less /etc/fstab

then look for the drive name there.

---

### Post by tarek on 2007-04-11
> **xsprayx313 said:**
> When trying to do so, i get /dev/hda1 does not exist


let's create the folder first: sudo mkdir /media/windows

hda1 is the first PARTITION in the first HARD DISK
so:
hda* is the * partition in the first hard disk

hdb is the second hard disk and so on.

to find out which hard disk/partition your windows files are on, run this command: sudo fdisk -l

your windows partition should be ntfs or fat

now run the command: sudo mount /dev/[hd**] /media/windows/ -t ntfs -o nls=utf8,umask=0222


where ** is the hard disk letter and partition number

tarek

---

### Post by xsprayx313 on 2007-04-11
Im really new, so i've gone thru a few things and just listed what it said to do.. so can you try to tell me :-\ sorry.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=541dd351-302d-4b96-8cfc-6ae9eee28ea0 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/sda5
UUID=3a7228f9-27ee-488f-bf79-2d631e3ef14a none            swap    sw            
  0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows ntfs umask=0222 0 0


it looks like theres hda1 ... but maybe the sd2?

---

### Post by tarek on 2007-04-11
Can you run this command please: sudo fdisk -l

post the output

thanks
tarek

---

### Post by xsprayx313 on 2007-04-11
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10115    81248706    7  HPFS/NTFS
/dev/sda2           10116       14746    37198507+  83  Linux
/dev/sda3           14747       14946     1606500    5  Extended
/dev/sda5           14747       14946     1606468+  82  Linux swap / Solaris

---

### Post by tarek on 2007-04-11
> **xsprayx313 said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10115    81248706    7  HPFS/NTFS
/dev/sda2           10116       14746    37198507+  83  Linux
/dev/sda3           14747       14946     1606500    5  Extended
/dev/sda5           14747       14946     1606468+  82  Linux swap / Solaris

Great! 

now run this command:
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

and browse to /media/windows/

let me know how it goes...

tarek

---

### Post by xsprayx313 on 2007-04-11
Wonderful, thank you so much <3

---

### Post by xsprayx313 on 2007-04-11
btw im sorry for hijacking this persons thread, but if he ever needed to know about any of this now he does :-D.

---

### Post by xsprayx313 on 2007-04-11
Sorry for three posts, question.. Everytime I reboot i'm going to have to do that code?

---

### Post by tarek on 2007-04-11
Don't be sorry!!! we all have questions :) 

We're gonna have to edit /etc/fstab so first back it up:
sudo cp /etc/fstab /etc/fstab_backup

next run this command to edit the file:
gksudo gedit /etc/fstab

finally copy this line to the end of the file, save and close:
/dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

The next time you restart it will mount automatically.

Don't hesitate to ask questions, someone must have the answer...

tarek

---

### Post by david_kt on 2007-04-15
> **glebreton said:**
> I have recently installed Ubuntu on a partition on my laptop on which I was running XP.
The dual boot works great!
However, I can't access my old c: drive. Is there any way I can change that now? 
I seem to be having some problems with wine because of this.
Thanks in advance,
Glebreton

If you want to run program in wine, you do not need your windows partition at all. Wine should work independently, and even if you need some files from windows, you could just downloaded it from internet. So, unless you want to read some of your files in windows, you do not need to access your windows c: drive at all.

DK

---

