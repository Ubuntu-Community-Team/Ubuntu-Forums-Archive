---
title: "How to auto mount disks at startup?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-06-09
Hi guys! I'm on Feisty and I would like to automount some partitions I have on my hdd. They are fat32. I'm sick to have to mount it and write the password every time I log on.  I guess there have to be some way to auto mount it, right?


Thank you mates!

---

### Post by gene74 on 2007-06-09
Thanks to Freebird54 for the links.

[http://ubuntuforums.org/showthread.php?t=465789](http://ubuntuforums.org/showthread.php?t=465789)

[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)


i just followed both guides and were able to mount both my HD and made them auto mount everytime.

---

### Post by Kosimo on 2007-06-09
Brilliant ;)

Thanks!

---

### Post by 3rdalbum on 2007-06-09
I'm assuming that you know the device file names of the partitions, since you're mounting them manually? I'll **illustrate an example** using /dev/sda2 as the partition and /media/sda2 as the mount point.

So, use Gedit to open the /etc/fstab file as root:

```
gksudo gedit /etc/fstab
```

Then put this into the bottom of it:

```
/dev/sda2	/media/sda2	vfat	defaults,utf8,umask=007,gid=46	0	1
```

Of course, you would replace these with your real device file and the real mount point.

When you reboot, you'll have the partitions automounted.

---

### Post by Kosimo on 2007-06-09
Hi, thanks for the answer.

But, how can I know the device file names?  From all tutorials I found around, yours seems to be the easiest one.  



:popcorn:

---

### Post by Efros on 2007-06-09
start terminal and type 
> 
sudo fdisk -l

---

### Post by bodhi.zazen on 2007-06-09
The above command gives you a list of your partitions.

You get to choose the mount point :)

The mount point must exist and typically /media is used (in Ubuntu).

so /media/<whatever name you like>

To make a mount point, you need to mkdir.

so to mount /dev/hda1 at /media/music

```
sudo mkdir /media/music
mount /dev/hda1 /media/music
```

If you understand this, fstab is a snap

**partition to mount**  - *mount point* -  **file system (ntfs,vfat,ext3)** - *options* - 0 2

The 0 = old back up method and is no longer needed.

The 2 = check file system on boot
0 = no
1 = check first, used for /
2= check after root, used for all the rest (there is no 3,4,5 ...)

---

### Post by Kosimo on 2007-06-09
> **bodhi.zazen said:**
> The above command gives you a list of your partitions.

You get to choose the mount point :)

The mount point must exist and typically /media is used (in Ubuntu).

so /media/<whatever name you like>

To make a mount point, you need to mkdir.

so to mount /dev/hda1 at /media/music

```
sudo mkdir /media/music
mount /dev/hda1 /media/music
```

If you understand this, fstab is a snap

**partition to mount**  - *mount point* -  **file system (ntfs,vfat,ext3)** - *options* - 0 2

The 0 = old back up method and is no longer needed.

The 2 = check file system on boot
0 = no
1 = check first, used for /
2= check after root, used for all the rest (there is no 3,4,5 ...)


Hi! That's a very logical way, I got it.  But I'm having some problems. I mounted a unit sda5 called music (for example) but I'm having problems with the encode of the namefiles, (I'm using international letters). There is some mount option about this?

So, now that I understand how to mount partitions, I'm still looking how to auto mout it.  I follow the guide posted above by 3rdalbum but I don't know how to get the exact numbers of my drive.


If it helps this is what I got when sudo fdisk -l: 

cosimo@cosimo-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1543    12394116    c  W95 FAT32 (LBA)
/dev/sda2            1544        6802    42242917+   f  W95 Ext'd (LBA)
/dev/sda3            6803        9729    23511127+  83  Linux
/dev/sda5            1544        6670    41182596    b  W95 FAT32
/dev/sda6            6671        6802     1060258+  82  Linux swap / Solaris

The partition I want to automount is the sda5.  Any idea?

Thanks again to everyone! :-P

---

### Post by bodhi.zazen on 2007-06-09
In the "options" column you need to add "auto" rather the "defaults" and add the appropriate information regarding encoding. 

For language you need :

nls=xxx (fat)

or

locale=xxx (ntfs)

---

### Post by ugm6hr on 2007-06-09
I still find this the best tutorial on auto-mounting internal drives (also has NTFS/ext3 advice):
[http://www.psychocats.net/ubuntu/mountwindows#fat32](http://www.psychocats.net/ubuntu/mountwindows#fat32)

Just substitute "/dev/hdb1" for "/dev/sda5" and "/fat_files" for "/media/*your_choice_of_name*"

---

