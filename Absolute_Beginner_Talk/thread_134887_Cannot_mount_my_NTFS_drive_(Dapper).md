---
title: "Cannot mount my NTFS drive (Dapper)"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by Clark Nova on 2006-02-22
I have upgraded my repositories list and done upgraded from a fresh install of Breezy to Dapper Flight 4. I'm trying to put my system back to how it was before but I can't seem to mount my NTFS drive again. I have followed the instructions I got in [http://www.ubuntuforums.org/showthread.php?t=129836](http://www.ubuntuforums.org/showthread.php?t=129836)[]("this thread") but I just can't seem to get my drive to mount again as it was before. 

If I type sudo fdisk -l I get:

```
Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        2550    20474842+   f  W95 Ext'd (LBA)
/dev/hda2   *        2551       20023   140351841    7  HPFS/NTFS
/dev/hda5               2        2550    20474811    7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4791    38483676   83  Linux
/dev/hdb2            4792        4998     1662727+   5  Extended
/dev/hdb5            4792        4998     1662696   82  Linux swap / Solaris

Disk /dev/sda: 524 MB, 524288000 bytes
255 heads, 63 sectors/track, 63 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          63      506016   83  Linux

```

I want to mount dev/hda2 but I just can't seem to do it. Is there another way to mount a drive other than at the command line?

---

### Post by Coelocanth on 2006-02-22
What command are you using to mount it?

Take a look at [This Guide](http://www.psychocats.net/linux/mountwindows.php) and see if it helps.

---

### Post by super on 2006-02-22
try this in a terminal:

> sudo umount /dev/hda2
sudo mkdir /Windows
sudo gedit /etc/fstab

then insert this line in your fstab (the window that your last command opened)

```
/dev/hda2	/Windows        ntfs	nls=utf8,umask=0222        	0       0
```

save and exit. then enter this in the terminal:

```
sudo mount /dev/hda2
```

and your windows partition should work. next time you reboot, this will be done automatically.

*note - you may be prompted to enter your password a few times

---

