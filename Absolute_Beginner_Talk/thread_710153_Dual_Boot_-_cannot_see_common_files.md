---
title: "Dual Boot - cannot see common files"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by jnorris235 on 2008-02-28
I've been forced to put XP on in order to use itunes.
Thanks to the forums it went perfectly.
Except that when in Ubuntu I can't see/access the common partition that has all my music on (sda3). XP sees it fine.

This is what I did:
/dev/sda1  /media/sda1   ntfs 10g  This has Windows XP on
/dev/sda2  extended
   /dev/sda5   /   ext3   10g   This has Ubuntu on
   /dev/sda6   linux-swap  2g
/dev/sda3   /windows   fat32   28g   This has my music on
/dev/sda4   /home   ext3   7g   This is my Ubuntu documents etc

In Ubuntu I can't see sda3
sda1 is mounted on the Desktop (don't really need to see  this one!)

sda5 and 6 are in the extended sda2 simply because the partition editor wouldn't let me have more than 4 partitions. I've no idea of the difference between extended and logical!

In Terminal sda1, 3, 4, 5 are listed (though 5 says: errors=remount ro)

XP and Ubuntu both work perfectly otherwise. 
So how can I get to see sda3 the fat32 partition please?

---

### Post by jken146 on 2008-02-28
Please post the outputs of the following commands:

```
sudo fdisk -l

cat /etc/fstab

mount
```

---

### Post by ruy_lopez on 2008-02-28
You might have to add /dev/sda3 to /etc/fstab

something like this:

```

/dev/hda3        /media/music        vfat        defaults        0        0

```

After adding this you'll need to create the mountpoint /media/music before rebooting.

---

### Post by jken146 on 2008-02-28
That's pretty much where I was going.

By the way, that should be **s**da3, not hda3.  If in doubt, type **sudo fdisk -l**.

To create that mount point, type ```
sudo mkdir /media/music
```

FYI, stuff that's mounted in /media is displayed by GNOME on the desktop and in the Places menu.

Also, no need to reboot.  Just unmount the partition: ```
sudo umount /dev/sda3
```
... and mount it again according to fstab: ```
sudo mount -a
```

---

### Post by jnorris235 on 2008-03-02
By the way - sorry for not getting back sooner - I'm supposed to get email notifications of replies, but never do!

OK, jken146 - did as you asked. How trusting was I - I thought fdisk reformatted the disk!!
Still only have sd1 on my desktop - hope this helps you!!

>>sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dfc2dfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/sda2            1217        2675    11719417+   5  Extended
/dev/sda3            2676        6322    29294527+   b  W95 FAT32
/dev/sda4            6323        7296     7823655   83  Linux
/dev/sda5            1217        2432     9767488+  83  Linux
/dev/sda6            2433        2675     1951866   82  Linux swap / Solaris

jon@chi:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=22a9176b-7481-4174-8170-e64fed59b43b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=9097ffa0-11ec-481e-a67f-f19261ad6095 /home           ext3    defaults        0       2
# /dev/sda1
UUID=14C4E4DAC4E4BF5C /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=BB88-9D40  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=bea042e5-1b82-49b5-8ec1-5f90e377fb7e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


jon@chi:~$ mount
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda4 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda3 on /windows type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=jon)

---

### Post by jnorris235 on 2008-03-02
My fstab already has this line:

# /dev/sda3
UUID=BB88-9D40  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1

I wasn't sure between you of the order of things to do, so I did this>>
sudo mkdir /media/music
sudo umount /dev/sda3
mount -a

and didn't do this>>
/dev/hda3        /media/music        vfat        defaults        0        0

I'll now reboot since nothing has appeared on the desktop.

---

### Post by logos34 on 2008-03-02
> **jnorris235 said:**
> and didn't do this>>
/dev/hda3        /media/music        vfat        defaults        0        0

I'll now reboot since nothing has appeared on the desktop.

No, you want 

> /dev/[COLOR="Red"]**s**[/COLOR]da3        /media/music        vfat        defaults        0        0

or 

> # /dev/sda3
UUID=BB88-9D40 **/media/music** vfat defaults,utf8,umask=007,gid=46 0 1

---

### Post by jnorris235 on 2008-03-02
Actually I did use sda not hda (just cut'n'pasted it wrong onto the reply box here).
After I did all that I got an extra DVD drive icon on my desktop but still no sda3!

Rebooted again and that extra one disappeared.
Then did this>>
/dev/sda3        /media/music        vfat        defaults        0        0

My fstab now has this>>
UUID=14C4E4DAC4E4BF5C /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=BB88-9D40  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda3        /media/music        vfat        defaults        0        0

Maybe I was supposed to replace it, not add it??

STOP PRESS
I can in fact navigate to the folder in (Places) and see the music files!!
Would like an icon if that is easy on the desktop (like sda1 does)

---

### Post by logos34 on 2008-03-02
You have two entries for the same partition.  Comment out (or delete) the original:

> # /dev/sda3
[COLOR="Red"]**#**[/COLOR]UUID=BB88-9D40 /windows vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda3 /media/music vfat defaults 0 0

ctrl+alt+backspace

hopefully icon will show up on desktop

---

### Post by jnorris235 on 2008-03-02
Perfect - thank you for your time, peoples!

---

