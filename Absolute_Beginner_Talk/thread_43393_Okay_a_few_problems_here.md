---
title: "Okay a few problems here"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by areadenial on 2005-06-21
I have used the command line before but I've only used Linux maybe 3 days now? I hope I am not breaking this boards rules.. 
> If you have previous experience with Linux (even if it just a little bit) or you have ever used the command line in your life to do tasks
If I am feel free to move this.


I also want to say as someone who is completely new to Linux, I am amazed at how friendly the community that surrounds it is... Ahem.. Now that I am done ass kissing hah here is the point..


My first issue would be:
1. I am having some issues with mounting drives/partitions. They dont seem to show up in the "Computer" section or in Places or anywhere else besides the /mnt/ folder.

If I go into fstab quickly I will see(I am going to copy the main two parts that apply to this)
```

/dev/sda1 /mnt/cdrive ntfs umask=0222 0 0
/dev/sda2 /mnt/ddrive vfat umask=0777 0 0

``` 
sda1 would be my XP directory
sda2 would be the fat32 partition I made if I ever decided one day I needed to step back into XP for a second or two.

Now if I go into the mnt directory I see cdrive with the windows install inside of it. If I go to ddrive(which has a red x'i cant see shit!' on the top right of it) and I cant get access to it. Okay umm.. right now I just tried right clicking that folder to see its properties and it disappeared....

I have followed the automount tutorials on that one guide website and I have tried > sudo mount -a enough times that if I had a penny for each time I did it, I'd have maybe about 11 pennies. Not that I was sitting there spamming that command.

when I type in fdisk -l I get

> 
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1355    10884006    7  HPFS/NTFS
/dev/sda2            6533       30394   191671483+   c  W95 FAT32 (LBA)
/dev/sda3   *        1356        6155    38556000   83  Linux
/dev/sda4            6156        6532     3028252+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9728    78140128+   7  HPFS/NTFS
 
--
The subproblem to this is that my iPod as well as my External HDD(both using firewire) are not detected at all.. fdisk doesn't even make note of them.


[I]
The next issue I am having is that when I boot up the system(No installer wanted to be installed on the main HDD so I installed it on my secondary HDD(hdb1) and it worked flawlessly.. The main problem is I cant figure out how to get it so that when I boot I dont have to always edit the linux partition from (hd1,1) to (hd0,1) so it'll boot correctly. How do I change this? I am using the GRUB loader.[/I] Nevermind that.. Realized I could edit it in the .lst file

If any other information has been left out that is important for fixing any of my problems I'll be happy to supply whatever info is needed.

----
I apologize these questions have been asked so many times.. I have been looking around in other threads at the problem I have been having but have found no luck in fixing it and I dont believe in hijacking people's threads.

---

### Post by xmastree on 2005-06-21
[QUOTE=areadenial]
sda1 would be my XP directory
sda2 would be the fat32 partition[/QUOTE]Assuming that XP is on a primary partition on your primary master disk, I suspect it ought to be /dev/hda1
A second partition, containing a virtual drive would be /dev/hda5

---

### Post by areadenial on 2005-06-21
[QUOTE=xmastree]Assuming that XP is on a primary partition on your primary master disk, I suspect it ought to be /dev/hda1
A second partition, containing a virtual drive would be /dev/hda5[/QUOTE]

Well I am able to access the XP partition just fine if I go to mnt->cdrive. Everything is in there so I am sure the sda1 line is correct. What is strange though is that I rebooted the computer a while after making this post and noticed that there was the cdrive disk icon on my desktop and in the Places tab. The sda2(ddrive) was nowhere to be found outside of the mnt directory.

I rebooted the computer again and was greeted by the cdrive icon no longer on my desktop or in the Places tab. I am now able to access both cdrive and ddrive now with all the proper files in them. They just dont show up on the desktop and in the Places menu.

Edit:

Here is how the full fstab looks

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               reiserfs notail          0       1
/dev/sda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/sda1 /mnt/cdrive ntfs umask=0222 0 0
/dev/sda2 /mnt/ddrive vfat umask=0222 0 0


---

### Post by poofyhairguy on 2005-06-22
[QUOTE=areadenial]--
The subproblem to this is that my iPod as well as my External HDD(both using firewire) are not detected at all.. fdisk doesn't even make note of them.

[/QUOTE]

Can you manually mount the ipod. (ask me how if google won't tell you and I'll look). This knowledge would help a LOT.

---

### Post by areadenial on 2005-06-22
[QUOTE=poofyhairguy]Can you manually mount the ipod. (ask me how if google won't tell you and I'll look). This knowledge would help a LOT.[/QUOTE]
 Yeah I can do that.. I think I pin pointed the problem to being purely an issue with firewire.

USB works fine and it mounts itself. Firewire and I have no luck. I dont mind the iPod being USB only but the external HDD I really would like to be on firewire..

---

