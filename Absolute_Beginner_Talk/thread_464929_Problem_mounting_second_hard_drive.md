---
title: "Problem mounting second hard drive"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by MightyFrog on 2007-06-05
I'm having a very frustrating morning. I just installed Ubuntu on my old computer and it's not recognizing my secondary IDE hard drive. The physical drive is listed under hardware information, but I can't figure out how to make the OS recognize the drive.  I tried 

mount /dev/hdb

and got the following:

"Can't find /dev/hdb in /etc/fstab or /etc/mtab."

Why is this so hard? All I want it to do is recognize an already formatted, partitioned, plugged-in hard drive. :(

---

### Post by Tux Aubrey on 2007-06-05
If the drive was detected when you installed, the partitions should be listed in the file /etc/fstab. (open it with a text editor)

Each partition will appear on a new line prefaced with an UUID number (if you are using edgy or feisty).  My hdb3 appears like this:

> # /dev/hdb3
UUID=4a73775b-b167-4513-9d88-e83c841d1192 /media/hdb3     ext3    defaults        0       2

Notice that the mount point is /_**media**_/hdb3 (not /_**dev/**_hd3b).

If your fstab has them listed, they should be mounted already.

---

### Post by taurus on 2007-06-05
Post

```
sudo fdisk -l
```

---

### Post by MightyFrog on 2007-06-05
OK, here's the fstab file

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=66ac58ff-4d18-4427-a7f6-75d9775e41f3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8c05d901-87a5-4fcb-b00b-b8690e3bd62e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

. . . and here are the fdisk results. Thank you for the responses.

```

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3533    28378791   83  Linux
/dev/hda2            3534        3649      931770    5  Extended
/dev/hda5            3534        3649      931738+  82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1023     8217243   54  OnTrackDM6

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48640   390700768+   c  W95 FAT32 (LBA)
```

---

### Post by taurus on 2007-06-05
Which drive are you trying to mount, /dev/hdb1 or /dev/sda1?

---

### Post by MightyFrog on 2007-06-05
I'm trying to mount /dev/hdb1. 

/dev/sda1 is an external USB drive that's recognized just fine.

---

### Post by taurus on 2007-06-05
Open gparted, System -> Administration, and see what does gparted have to say about /dev/hdb1 (filesystem).  And if you don't have gparted on your system, install it with

```
sudo aptitude update
sudo aptitude install gparted
```

Do you have anything on /dev/hdb1?

---

### Post by MightyFrog on 2007-06-05
gparted tells me that there's 7.84 gigs in an unknown filesystem and 68.49 gigs unallocated. I'm not sure what unallocated means, I'm afraid.

---

### Post by taurus on 2007-06-05
Sounds like you need to merge both into one partition and format it to whatever filesystem you want to use first before you can mount it.  You can do all that with gparted.

---

### Post by aeiah on 2007-06-05
what were you expecting to find on there? it seems the drive is slightly corrupted if you expected something else. did you partition it in windows?

you could try using gparted to fix the partitions (or whichever partition editor you used to partition it initially).

i found the best gparted results by using the gparted livecd. its only 50mb and is a newer version than the one in the ubuntu repository, but see if you can get results with the gparted you have on your system first.

---

### Post by MightyFrog on 2007-06-05
:( :( :(

I had a lot of older material on that drive--nothing crucial, but some music files that I didn't have backed up elsewhere. My reason for installing Ubuntu on that computer was that the WinXP installation had gotten hopelessly slow and twitchy. Does it seem like the Linux install borked the drive?

---

### Post by taurus on 2007-06-05
I don't think Ubuntu borked the drive.  Looks like you wiped out XP while installing Ubuntu on the first drive.

---

### Post by mips on 2007-06-05
```

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1023     8217243   54  [COLOR=Red]**OnTrackDM6**[/COLOR]

```

You are using a non standard file system. To mount that drive follow these instructions:
[http://ramses.smeyers.be/varia/OnTrackDM6/](http://ramses.smeyers.be/varia/OnTrackDM6/)
[http://ubuntuforums.org/showpost.php?p=2315754](http://ubuntuforums.org/showpost.php?p=2315754)

It will be read only, backup your data and delete all partitions on the drive and reformat.

---

### Post by ghanu on 2007-06-05
Evn I had the same prob like unallocated partition but it was due to unformatting of the partition so i think u need to format the second partition of hdb ...n for mounting first partition 
mount /dev/hdb1 /mnt/
shud be okay....n look for the same in /etc/mtab after mounting ..copy this line into /etc/fstab so that it mounts automatically on each boot...

---

### Post by mips on 2007-06-05
> **ghanu said:**
> Evn I had the same prob like unallocated partition but it was due to unformatting of the partition so i think u need to format the second partition of hdb ...n for mounting first partition 
mount /dev/hdb1 /mnt/
shud be okay....n look for the same in /etc/mtab after mounting ..copy this line into /etc/fstab so that it mounts automatically on each boot...

Ignore this if you want to recover any data.

---

### Post by MightyFrog on 2007-06-05
OK, a clarification: these were the instructions on the thread that mips pointed me to.

> Use the following instruction to mount an type OnTrackDM6 partition in Linux.

/dev/hdb1 * 1 1653 833111+ 54 OnTrackDM6

Adapt your bootloader and add the option hd<x>=remap63 for your kernel where x is your disk.

Now reboot your system and the partition is visibale as (for example)

/dev/hdc1 * 1 826 832576+ 6 FAT16

Should I insert "sudo mount" before the command "/dev/hdb1 * 1 1653 833111+ 54 OnTrackDM6"? Just typing the string gives me an "unknown command." I also tried it with hdb instead of hdb1.

---

### Post by MightyFrog on 2007-06-05
Bump for the nighttime crowd.

---

### Post by MightyFrog on 2007-06-07
Unfortunately, the data on the hard drive is indeed gone. I pulled the drive and stuck it in a Windows box; aside from a little proprietary partition that came installed with the drive, the data is gone. I'd like to understand how this happened. I wasn't able to back up this data before installing Ubuntu because my WinXP had gotten so unreliable. Still, the data was there before I installed Ubuntu. Again, the Ubuntu installation was on a *different* hard drive in this computer--why did I lose the data on a drive that wasn't getting anything installed on it?

---

### Post by domer on 2007-06-07
Here is the [COLOR="Red"]**SOLUTION**[/COLOR]


Hello all,

I also had similar problems and after trying different forums and messing with my Ubuntu installation I reached a point where I formatted my Ubuntu partition and reinstalled it. Then I bumped on this site [http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop) which described the mounting phenomenon in simple words and precisely defined what I need to do to gain access to my second hard drive as well as my windows partition on the same disk as Ubuntu.

I hope this helps others just like it helped me. 

Cheers!!

---

### Post by =JeffH on 2007-06-08
thanks for pointer to that disk mounting page. 

Here's another post that folks might find helpful...

[http://ubuntuforums.org/showpost.php?p=2806660&postcount=4](http://ubuntuforums.org/showpost.php?p=2806660&postcount=4)


=JeffH

---

