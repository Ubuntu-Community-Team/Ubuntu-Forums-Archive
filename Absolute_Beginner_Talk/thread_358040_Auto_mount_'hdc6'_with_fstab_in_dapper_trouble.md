---
title: "Auto mount 'hdc6' with fstab in dapper trouble"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by phil54601 on 2007-02-10
Hello;
I recently re-installed dapper on my primary HDD (hda3) in an IBM t-23 laptop.  I have a second HDD installed as (hdc) in the ultra2000 bay.  Before the re-install I was able to access hdc6.  Now I can't.  This is the bottom 1/2 of my fstab file:
******************************
# These segments are on the Linux 48GB drive
# partition /dev/hda7  is the Swap partition do NOT mount it.
/dev/hda5  /home/phil/Linux2 ext3 umask=0000		    0       0
/dev/hda6  /home/phil/LinWin vfat umask=0000 		    0       0

# This segment is for the Win2000 60GB drive
/dev/hdc6  /home/phil/Drv_E_on_60GB_Disk  vfat auto, uid=1000, gid=1000     0       0
/dev/hdc7  /home/phil/Future_Linux_disk#2  vfat defaults, uid=1000, gid=1000     0       0


#/dev/hdc6  /home/phil/Drv_'E'_on_60GB_Disk  vfat umask=0000    0       0
#/dev/hdc6  /home/phil/Drv_'E'_on_60GB_Disk  vfat user    0       0
#/dev/hdc6  /home/phil/Drv_'E'_on_60GB_Disk  vfat defaults, uid=1000, gid=1000    0     0 
#/dev/hdc7  /home/phil/Future_Linux_disk#2  vfat umask=0000     0       0
#/dev/hdc8  /home/phil/Drv#2_hdc8'G' vfat umask=0000     0       0
******************************
All 7 lines referencing hdc fail.  Either the drive doesn't mount or it's owned by 'root'.

Before the re-install this line worked (I was owner):
/dev/hdc6  /home/phil/Drv_'E'_on_60GB_Disk  vfat  uid=1000, gid=1000    0       0

In a terminal the command (sudo mount -a) gives these results:
******************************
[mntent]: line 18 in /etc/fstab is bad
[mntent]: line 19 in /etc/fstab is bad
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
******************************

The fdisk command (phil@phil-T23:~$ sudo fdisk -l /dev/hdc) provides these lines:
******************************
/dev/hdc6            3388        3794     3076888+   b  W95 FAT32
/dev/hdc7            4172        5120     7164958+   b  W95 FAT32
******************************

As you can see I'm trying to mount these drives under /home/phil/.  This probably isn't correct.  Ive seen drives mounted under /dev,  /mnt, and /media.   Where is the correct place?
I'm in over my head.  Please help me sort all this out.
Thank You
Phil

---

### Post by po0f on 2007-02-10
phil54601,

Spaces aren't allowed between the mount options.  You should change this:

```
[FONT="Courier New"]# This segment is for the Win2000 60GB drive
/dev/hdc6 /home/phil/Drv_E_on_60GB_Disk vfat [color="red"]auto, uid=1000, gid=1000[/color] 0 0
/dev/hdc7 /home/phil/Future_Linux_disk#2 vfat [color="red"]defaults, uid=1000, gid=1000[/color] 0 0[/FONT]
```

to this:

```
[FONT="Courier New"]# This segment is for the Win2000 60GB drive
/dev/hdc6 /home/phil/Drv_E_on_60GB_Disk vfat [color="green"]auto,uid=1000,gid=1000[/color] 0 0
/dev/hdc7 /home/phil/Future_Linux_disk_2 vfat [color="green"]defaults,uid=1000,gid=1000[/color] 0 0[/FONT]
```

I also changed the mount point for /dev/hdc7 from "/home/phil/Future_Linux_disk#2" to "/home/phil/Future_Linux_disk_2".  I don't think hash characters are allowed in filenames.

---

### Post by phil54601 on 2007-02-10
Hello;
I tried your suggestions.  This  is my current fstab.  
/dev/hdc6  /home/phil/Drv_E_on_60GB_Disk  vfat auto,uid=1000,gid=1000     0       0
/dev/hdc7  /home/phil/Future_Linux_disk_2  vfat defaults,uid=1000,gid=1000     0       0

This line was mounting,but it was owned by root:
 /dev/hdc8  /home/phil/Drv#2_hdc8_G vfat umask=0000     0       0
I changed it to: 
 /dev/hdc8  /home/phil/Drv_2_hdc8_G vfat umask=0000     0       0

I may have missed something.  Even with the hdc8 line commented out.   I'm still getting this error:
phil@phil-T23:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
phil@phil-T23:~$

Also what is ythe difference between the use of:
auto,uid=1000...
defaults,uid=1000...

Does mixing the 'uid=1000' form and the 'umask=0000' form cause problems?
Thanks again.
Phil

---

