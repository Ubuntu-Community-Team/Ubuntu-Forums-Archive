---
title: "Mount EZ-Drive System (NTFS) Hard Drive"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by fzfrank on 2007-01-09
This is my second try installing Ubuntu in as many days. I've figured a bunch of stuff out on this forum but I'm having trouble mounting a Windows NTFS drive. Yesterday I gave it a try based on some of the comments in this forum (I understand the risks) and the next time I tried to boot, the system hung on something like “mounting root file system.”  It's possible that the Ubuntu drive went bad because I tried to re-install Ubuntu on that drive and it hung at 15% twice.

In any case, I reinstalled Ubuntu on hdb, my windows boot disk is hda, and I want to access (read only) hdd. The thing that scares me is that “fstab” reports the system of hdd as EZ-Drive – I've never heard of that. I searched for EZ-Drive on this forum and found only one irrelevant entry.

I was thinking about doing
```
mkdir /media/200g_drive

mount /dev/hdd1 /media/200g_drive/ -t ntfs -r -o umask=0222

update /etc/fstab
```

Then add the following to /etc/fstab:

```
/dev/hdd1 /media/200g_drive ntfs ro,defaults,umask=0222 0 0
```

Will that do it? I'm a little concerned about that EZ-Disk system.

FYI, here is the output of sudo fdisk -l

[HTML]Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14589   117186111    7  HPFS/NTFS

Disk /dev/hdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1162     9333733+  83  Linux
/dev/hdb2            1163        1216      433755    5  Extended
/dev/hdb5            1163        1216      433723+  82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1023     8217243   55  EZ-Drive

[/html]

...and here is the contents of etc/fstab
[html]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0[/HTML]

FYI, hdd and hdd1 show up in the /dev directory. The mnt directory is empty.

Any help would be appreciated.

---

### Post by fzfrank on 2007-01-09
Update:

I tried ```
sudo mount /dev/hdd1 /media/200g -t EZ-Drive -r -o unmask=0222
```
and got:
```
mount: unknown filesystem type 'EZ-Drive'
```

I also tried ```
sudo mount /dev/hdd1 /media/200g -t ntfs -r -o unmask=0222[
```
and got:
```
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

No damage done, but I still can't mount the drive.

---

### Post by fzfrank on 2007-01-09
I'm still working on this. Someone told me that I needed to add the grub option "hdd=remap". If I insert that command before the boot command I get "unrecognized command" (or something like that. If I insert it after the boot command, nothing happens.

Does that help?

---

### Post by fzfrank on 2007-01-10
Ok, I got it. I was trying to make the change in the wrong place on Grub. I added hdd=remap to the kernel line, did all that other stuff and BAM I mounted the drive.

Now all I need to know is how to make that change to the kernel permanent. Anyone?

---

### Post by fzfrank on 2007-01-11
In case anyone runs into this problem, here was my solution:
Keep in mind, I'm a 2-day old noob, so you might want to confirm this before you risk all your data.

Do this:
```
cd /boot/grub
sudo cp menu.lst menu_backup.lst
sudo gedit menu.lst
```

Add "hdd=remap" to the end of the Kernel line 
(obviously you would replace hdd with your drive)
I added the command to the kernel I boot to, but I suppose you could add it to all of them.

Save and exit

Then do:
```
sudo mkdir /media/200g (or whatever you want to call it)
```

Then do:
```
cd /etc
sudo cp fstab fstab_backup
sudo gedit fstab
```

Add the following to fstab:
```
/dev/hdd1       /media/200g     ntfs    ro,defaults,umask=0222 0 0
```

Save and exit. 

Reboot.

The drive should be mounted. It even showed up on my desktop.

---

