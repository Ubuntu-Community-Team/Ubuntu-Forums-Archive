---
title: "Mounting Windows Partition"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-19
I have followed this tutorial to mount my windows partition:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) 

However I do not see my windows partition Under Places > Computer (when i restart)

And the windows folder in media is empty

sudo fdisk -l:

```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3854    30957223+   7  HPFS/NTFS
/dev/hda2            3855        7152    26491185   83  Linux
/dev/hda3            7153        7296     1156680    5  Extended
/dev/hda5            7153        7296     1156648+  82  Linux swap / Solaris

Disk /dev/sda: 128 MB, 128450048 bytes
8 heads, 32 sectors/track, 979 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         979      125263+   6  FAT16
```

sudo nano /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows ntfs   nls=utf8,umask=0222     0       0
```

What did I miss?
Thanks.

---

### Post by bodhi.zazen on 2006-11-19
Small typo

In fstab, Change > /dev/hda1       **/windows** ntfs   nls=utf8,umask=0222     0       0

To> /dev/hda1       **/media/windows** ntfs   nls=utf8,umask=0222     0       0

then```
sudo umount /windows
sudo rm -r /windows
sudo mount /media/windows
```

---

### Post by taurus on 2006-11-19
But you mount it on /windows, not /media!!!  If you want to mount it to /media, then change your mount point from /windows in /etc/fstab to /media/windows.  Don't forget to create a new mount point for it as

```
sudo mkdir /media/windows
```

---

### Post by PartisanEntity on 2006-11-19
Thank you, it worked.

---

### Post by PartisanEntity on 2006-11-19
If I mount in media it will show up on my desktop is that correct?

What if I only want it to show up in Places > Computer ?

---

### Post by PartisanEntity on 2006-11-20
I don't want the drive icons to show up on my Desktop, I only want them to be listed in Places > Computer for example. How would I go about doing that?

Thank you.

---

### Post by slowmover on 2006-11-20
Hmm, ok, i did it like *PartisanEntity* and also with all the other additions
explaind in this thread here,
but when i want to mount it to /media/windows
it shows me the following error

> mount: wrong fs type, bad option, bad superblock on /dev/hda6,
missing codepage or other error

and with *dmesg* it shows me:
> NTFS-fs error (device hda6): parse_option(): Unrecognized mount

any help for a newbie ?

---

### Post by m.musashi on 2006-11-20
> **PartisanEntity said:**
> I don't want the drive icons to show up on my Desktop, I only want them to be listed in Places > Computer for example. How would I go about doing that?

Thank you.

If you use configuration editor you can specify this (are you using gnome?). I'm actually on KDE at the moment but I think you go to apps->nautilus->desktop and then deselect volumes_visible

---

### Post by PartisanEntity on 2006-11-21
Yes I am using gnome, but I can't find Nautilus under apps, do I have to install a frontend for it?

---

### Post by iLoVe.cF- on 2006-11-21
Terminal:
My example:

sudo fdisk -l

Mount ur selected drive.

sudo mkdir /media/Pata250GB
sudo mkdir /media/Pata200GB
sudo mkdir /media/Pata200GB2
sudo mkdir /media/Sata200GB
sudo mkdir /media/Sata250GB

This is just for my case of sorting.. maybe u like it..

sudo nano, i reccon gedit for newbs)--- read next line for my way :)
Sudo gedit /etc/fstab

/dev/hda5    /media/Pata200GB    ntfs  nls=utf8,umask=0222 0    0
/dev/hda     /media/Pata200GB2    ntfs  nls=utf8,umask=0222 0    0
/dev/hda     /media/Sata200GB    ntfs  nls=utf8,umask=0222 0    0
....

So on..

I found it RATHER better to delete som of ur useless files.. if you got the amount of drives as me..

Move everything to diff drives..
make one drive to ext3
then move on that one.. or convert to ext3 on nearly every drive.. leave something for windows if u like

Install support for linux filesystem in windows..

Ext crash less than ntfs

I CAN REALLY PROVE THIS.

Provement setup.
normal comp with an 60 gb wdc ide ata 100

WITH BROKEN POWER CONNECTOR.

This result in lots of hdd shutdowns/reboots while read/write.. and the ext3 survive much better :D

---

### Post by m.musashi on 2006-11-21
> **PartisanEntity said:**
> Yes I am using gnome, but I can't find Nautilus under apps, do I have to install a frontend for it?

No, it should install by default. You have to run configuration editor first. It may not show up on any of your menus. It should be under applications -> system tools. If not, you can add it by right clicking on applications and choosing edit menu (or similar - still on kde and can't verify). Add configuration editor and then run it. Follow the path to nautilus and uncheck the box next to volumes_visible. I do this every time I reinstall. I'll log into gnome and double check everything.

EDIT - okay, I'm in gnome. Configuration editor is the app you want. Add it to your menu like I described if you need to. I've attached a snapshot of the section of the app you need to change to hide the drive icons. Reply if you are still having problems.

Cheers.

---

### Post by PartisanEntity on 2006-11-22
Okay thanks very much, ill have a look when I get home from work.

---

