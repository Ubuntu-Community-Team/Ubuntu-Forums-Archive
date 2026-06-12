---
title: "Hello Everybody :)"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Jericho7 on 2006-05-24
Hi Everybody,
This is my first post, I'm a 33 years old pc techinicial/IT and I'm working at a IT company here in Athens/Greece.
I'm experience with all platforms of windows and MAC OS/10 but this is my first encounter with any kind of Linux.
Yesterday I've install the Ubuntu V5.10 through VMWARE in my PC and at first sight I'm very happy about it.

So here it is my first problem... :)

I have 6 Hard Disk in my pc (2 ATA and 4 SATA) and as I say I have installed Ubuntu through VMWARE, in a blank hard disk (giving a 10GB space for ubuntu) so my problem is I want to access the rest of my hard drives through Ubuntu, I've tried to mount it but unsuccessfully :(.
Can you tell me how?

Thanks in advance.


Michael.

---

### Post by ProjectGod on 2006-05-24
hello!

more information needed please... 6 hard disks!!! :shock: 
such as what do you have on the other 4 hard disks... IDE or SCSI?

try [https://wiki.ubuntu.com/InstallingANewHardDrive?highlight=%28hard%29%7C%28disk%29](https://wiki.ubuntu.com/InstallingANewHardDrive?highlight=%28hard%29%7C%28disk%29)

---

### Post by Jericho7 on 2006-05-24
The First one (400gb sata) is my windows xp disk.
The second one(400gb sata)is my programs disk
The third one (400gb sata) is my divx disk
The 4th one (400gb sata) is my mp3
the 5th one (200 gb ide) is my tmporay disk
and the 6th one (200 gb ide) is my vmware disk (includes the ubuntu, a mac OS 10, and a  MS tiny Windowx XP Pro directories ( 20gb each for every operating system).


Michael

---

### Post by ProjectGod on 2006-05-24
may i ask what the file systems on the disks 2 - 5 are? :mrgreen:

---

### Post by morequarky on 2006-05-24
I have never seen such a setup.  Seems nice.

"in my PC" you have 6 harddrives inside your computer.  NO USB or anything.  All the harddrives are inside the computer.

Which harddrive is "master"?

fstab will need to be configured I figure.

Are you using Ubuntu or Kubuntu?

System - Admin - Disk may be able to see them.

I think your going to love Ubuntu ultimately.

What are the file systems of the disk?  All NTFS?  Any Fat32?

I don't think I could fit 6 harddrives in my computer.  Are any harddrive outside the computer.

---

### Post by dmizer on 2006-05-24
if you've installed ubuntu via vmware, you should have a local ip for your ubuntu vm.  in that case, all you should need to do is enable samba file sharing to swap files across the network.

no idea how to get direct access to disks from a vm ... is that even possible?

---

### Post by ProjectGod on 2006-05-24
from the ubuntu terminal try:

sudo lshw -C disk

check to see if all your 6 disks are recognised by ubuntu. you should get details of them. :D

i heard you could only read mounted ntfs partitions... read write for FAT... 

**when you try to mount them what error message do you get?**

---

### Post by catlett on 2006-05-24
```
sudo fdisk -l
```
This command will list your hard drive and partitions. Here is mine for example 
> tj@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5099    40957686    7  HPFS/NTFS
/dev/hda2            6375       10270    31294620    f  W95 Ext'd (LBA)
/dev/hda3   *       10271       12161    15189457+  83  Linux
/dev/hda4            5100        6374    10241122+  a5  FreeBSD
Partition 4 does not end on cylinder boundary.
/dev/hda5            7798        8665     6972178+   b  W95 FAT32
/dev/hda6            8666        8795     1044193+   b  W95 FAT32
/dev/hda7            8796       10185    11165143+  83  Linux
/dev/hda8           10186       10270      682731   82  Linux swap / Solaris
/dev/hda9            6375        7797    11430184+  83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 128 MB, 128450560 bytes
8 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         979      125296    6  FAT16

Disk /dev/sdd: 129 MB, 129990656 bytes
16 heads, 16 sectors/track, 991 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         990      126703+   6  FAT16

Disk /dev/sde: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        4865    39078081    c  W95 FAT32 (LBA)
Now that you know how Ubuntu sees them you can mount them. I'll show you how  to give a command to mount them that will manually mount the disk for 1 session. Next time around it will not be mounted.
First you need to make a directory to put the drives in. Use the media folder because this will put an icon on the desktop. This is an example, you can call the dirctory  whatever you want.
```
sudo mkdir /media/windows
sudo mkdir /media/divx
sudo mkdir /media/ mp3
```
Once you make the directories you mount with the mount command, the name of the drive or partition to mount, the filesystem type, where to mount.
I'll mount a couple of my partitions to the directories we made.
```
sudo mount /dev/hda2 -t vfat /media/windows
sudo mount /dev/hda7 -t ext3 /media/divx
```
I don't have sata so I dont know how it will be listed. Just use the way fdisk lists it. I.e. I used /dev/hda2 because that is how it is listed. Also the filesystem you need to know. If it is fat32 or fat you use vfat. I'm assuming you have nfts because of the size of you drives. So it would be ntfs where I put vfat and ext2 in my example. So it would look something like this 
```
sudo mount /dev/??? -t ntfs /media/mp3
``` You unmount by repeating the same command except using umount instead of mount. In this case the drives will be unmounted upon shutdown.
This link will walk you through how to permanently moiunt the drives. [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
This guide was for the version before Breezy but the commands still work the same [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)
You can mount ntfs but it is still questionable but if you're interested [http://ubuntuforums.org/showthread.php?t=142481&highlight=ntfs](http://ubuntuforums.org/showthread.php?t=142481&highlight=ntfs)

---

### Post by Jericho7 on 2006-05-24
Ok guys look....

All my hard disk is ntfs, I also have 4 usb 2 400gb external hard disk and 4 200gb usb 2 external hard disk (lol)
All hard disk is one partition only and my first hd is a sata 400gb with windows xp.
ubuntu is on 3rd sata cable. 

I know its a lot of space but i have a great collection of movies, mp3's, programms and  game images, so i use all of it (almost!!)

finaly can i use my external usb 2.0 hard disks also from linux?

Im at work right now, sow when i go back at my house i will check the above info you give me guys and.. I will tell you waht happen.

Thanks again for the quick answerings :)


Michael.

---

### Post by dmizer on 2006-05-24
you will be able to read ntfs, but i wouldn't advise you to try to write to ntfs from linux.  there are howto's around, but general consensus is that it's simply not safe.

---

### Post by catlett on 2006-05-24
If you have the  on  external usb/firewire enclosure it is automatic. I have one on a firewire and when I power on an icon appears automatically.
I just realised fdisk -l won't read all your drives. Fdisk has parameters for searching. I found this quickly. I'll post more later 
>  Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda (for the first IDE disk)
or: fdisk /dev/sdc (for the third SCSI disk)
or: fdisk /dev/eda (for the first PS/2 ESDI drive)
or: fdisk /dev/rd/c0d0 or: fdisk /dev/ida/c0d0 (for RAID devices)
Try this command  ```
sudo /sbin/fdisk -l 
``` This is supposed to list all drives but it doesn't notice my firewire. 
If they are external usb/firewire they should be mounted automatically.
To view the contents of youe /etc/fstab file run  ```
cat /etc/fstab 
``` This will only tell you the drives that are seen and mounted. You will deal with /ect/fstab when you follow the links.
Post if you have problems when you get to your Ubuntu vmware computer.

[COLOR="Red"]Edit ProjectGod has the right command[/COLOR] ```
sudo lshw -C disk
```
After you see how they are listed you mount by making a idrectory with mkdir (if you mount in /media, an icon will appear on the desktop). Then you use the mount command followed by what you want mounted /dev/???. Next is the option , use -t. Followed by the type of filesystem i.e. ext3 or ntfs etc. Lastly the place to mount it. (the place you made with mkdir) This is a generic command to mount other partitions or drives for a single session```
 sudo mount /dev/??? -t filesystem /media/???
```The links I posted will take more in depth, I just wanted to tie up a loose end.

---

### Post by Jericho7 on 2006-05-25
Guys I've tried everything you told me but the only think I can see is my cdrom and a VMWARE partition that's all nothing else :( :(
I also see that the vmware partiotion is partiotioned in 3  pieces the swap, the extended and the linux. :(

I can't see anything else :(

Maybe there is a "trick" to see it through the vmware?

Michael.

---

### Post by dmizer on 2006-05-25
which version of vmware are you using ... i still don't think it's possible to view host hdd from a vm.

---

### Post by nalmeth on 2006-05-25
I could see difficulties arising with extra HD's when in VMware. VMware is just virtualizing Ubuntu, so it is probably 'oblivious' to what's outside the Virtual Workstation. This could be wrong though, there might just be a trick, as you say.

Are you commited to running Ubuntu in VMware? I can think of many reason's why you might be, but the easiest thing to do would be to make room for it to go side by side with windows, or on another of your drives.

Also, the new release of Ubuntu (Dapper Drake 6.06) is due for release in less than 2 weeks, and it is already being used by many, including myself. If you're willing to reconsider your setup, think about installing 6.06. Although you can still upgrade from 5.10 if you'd prefer not.

BTW I like your avatar. Electrifying

---

