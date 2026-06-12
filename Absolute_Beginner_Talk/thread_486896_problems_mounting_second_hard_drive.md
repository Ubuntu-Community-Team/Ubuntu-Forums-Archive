---
title: "problems mounting second hard drive"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-06-28
I have followed the instructions at Mounting Linux Partitions/Drives in Ubuntu (/www.psychocats.net/) and am having trouble. When I edit fstab using:

/dev/hdb1 /storage ext3 defaults 0 0

And then use :
desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I run dmesg | tail I get:


tim3@tim3-desktop:~$ dmesg | tail
[  140.338055] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[  145.321441] eth0: no IPv6 routers present
[  759.580766] init_special_inode: bogus i_mode (600)
[  759.580798] EXT3-fs: invalid journal inode.
[  975.388674] init_special_inode: bogus i_mode (600)
[  975.388706] EXT3-fs: invalid journal inode.
[ 1067.047358] init_special_inode: bogus i_mode (600)
[ 1067.047389] EXT3-fs: invalid journal inode.
[ 1620.972707] init_special_inode: bogus i_mode (600)
[ 1620.972738] EXT3-fs: invalid journal inode.

Can anyone tell me where my problem is . . . okay besides a complete lack of knowledge.

Thanks, Tim 
Oh here is fdisk -l

 sudo fdisk -l

Disk /dev/hda: 13.6 GB, 13600000000 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1578    12675253+  83  Linux
/dev/hda2            1579        1653      602437+   5  Extended
/dev/hda5            1579        1653      602406   82  Linux swap / Solaris

Disk /dev/hdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         981     7879851   83  Linux
/dev/hdb2             982        1027      369495    5  Extended
/dev/hdb5             982        1027      369463+  82  Linux swap / Solaris

---

### Post by orb9220 on 2007-06-28
> /dev/hdb1 /storage ext3 defaults 0 0

Do you have a folder called **storage** to mount to?

If I wanted it to mount to storgage then I would /dev/hdb1 **/orb/storage** ext3 defaults 0 0
after I created a folder named storage in home.

---

### Post by Inxsible on 2007-06-28
I think the line should be
 
```
/dev/hdb1 /storage ext3 defaults 0 [COLOR=red]2[/COLOR]
``` but I am not sure that matters. I may be wrong

---

### Post by SVWander on 2007-06-28
> **Inxsible said:**
> I think the line should be
 
```
/dev/hdb1 /storage ext3 defaults 0 [COLOR=red]2[/COLOR]
``` but I am not sure that matters. I may be wrong

I gave it a try with the same error message:
@tim3-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Again I tried dmesg | tail:

@tim3-desktop:~$ sudo dmesg | tail
[ 6645.991012] init_special_inode: bogus i_mode (600)
[ 6645.991068] EXT3-fs: invalid journal inode.
[ 9029.318993] init_special_inode: bogus i_mode (600)
[ 9029.319025] EXT3-fs: invalid journal inode.
[ 9258.086125] init_special_inode: bogus i_mode (600)
[ 9258.086155] EXT3-fs: invalid journal inode.
[ 9301.406352] init_special_inode: bogus i_mode (600)
[ 9301.406383] EXT3-fs: invalid journal inode.
[ 9475.577252] init_special_inode: bogus i_mode (600)
[ 9475.577283] EXT3-fs: invalid journal inode.

I wonder what the EXT3-fs invalid journal means? I still cannot mount that second hard drive.  tm

---

### Post by nidoo on 2007-06-28
Hi 

Have you formatted you hdb1 EXT3 or is there another format left over from a previous installation?

If it's formated ext3 and all ready to go first create a directory to mount the drive to with
> sudo mkdir /media/hdb1 in the terminal.

(I use /media/hdb1, but you can use anything you want like /storage/hdb1)

Mount it by hand by using
> sudo mount -t ext3 /dev/hdb1 /media/hdb1

and for you /etc/fstab use
> /dev/hdb1 /media/hdb1 ext3 defaults 0 2

Hope this helps.:)

---

