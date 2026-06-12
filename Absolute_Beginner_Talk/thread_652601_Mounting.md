---
title: "Mounting"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by fishmonk on 2007-12-28
I just installed Ubuntu,

I can see my cd/dvd drive, and 2 different volumes, as well as the filesystem. I also have an usb external harddrive. When I try to access the external drive it says "cannot mount volume" I can access the smaller of the other volumes, but the larger one returns the same error and takes me to my file system. 
I'm very new at ubuntu, so I was hoping someone could give a step by step on how to access these drives.
I already went under system>Preferences>Removable Drives and tried unselecting the options there, but that didn't work.

---

### Post by PmDematagoda on 2007-12-28
Could you please post details about the external Hard Drive? And also what Filesystem does it have?

---

### Post by fishmonk on 2007-12-28
It's a usb 2.0 external hardrive 160 Gb made by Maxtor that works fine in windows. and I'm not sure by what you mean by which filesystem

---

### Post by PmDematagoda on 2007-12-28
Does it have any special mechanisms, or does it require any software on Windows?

---

### Post by fishmonk on 2007-12-28
No, it's just plug and play

---

### Post by PmDematagoda on 2007-12-28
When you plug the HDD into Ubuntu, could you post the result of:-
```
lsusb
```
and
```
sudo fdisk -l
```

---

### Post by fishmonk on 2007-12-28
Bus 005 Device 003: ID 0d49:3200 Maxtor 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

and

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         766        5635    39118275    7  HPFS/NTFS
/dev/sda2               1         765     6144831    b  W95 FAT32
/dev/sda3            5636        7220    12731512+  83  Linux
/dev/sda4            7221        7296      610470    5  Extended
/dev/sda5            7221        7296      610438+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5aba8b43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTF

---

### Post by PmDematagoda on 2007-12-28
Here is what you can do:-

1) Make a new directory in /media(You may replace "something" for whatever you want):-

```
sudo mkdir /media/something
```

2) Mount the drive(Replace "something" with the name you put for the directory):-

```
sudo ntfs-3g -t /dev/sdb1 /media/something
```

That should mount your drive, if it does not, post the complete error message you get.

---

### Post by fishmonk on 2007-12-28
It said this:
ntfs-3g: Unknown option '-t'.

ntfs-3g 1.913 - Third Generation NTFS Driver

Copyright (C) 2005-2006 Yura Pakhuchiy
Copyright (C) 2006-2007 Szabolcs Szakacsits

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro, force, locale=, uid=, gid=, umask=, fmask=, dmask=,
          streams_interface=. Please see details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force,locale=en_EN.UTF-8

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)
william@william-laptop:~$ sudo ntfs-3g -t /dev/sdb1 /media/HDD
ntfs-3g: Unknown option '-t'.

ntfs-3g 1.913 - Third Generation NTFS Driver

Copyright (C) 2005-2006 Yura Pakhuchiy
Copyright (C) 2006-2007 Szabolcs Szakacsits

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro, force, locale=, uid=, gid=, umask=, fmask=, dmask=,
          streams_interface=. Please see details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force,locale=en_EN.UTF-8

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)



When I try to access the drive again by double clicking on it it says the same thing as before:

$logfile indicates unclean shutdown (0,0) failed to mount '/dev/sdb1': operation not supported mount is denied because NTFS is marked to be in use. Choose one action: choice 1: if you have windows then disconnect the external evices by clicking on the safely remove hardware icon in the Windows taskbar then shutdown windows cleanly.

which I've tried.

---

### Post by PmDematagoda on 2007-12-28
Then use this command to mount:-

```
sudo ntfs-3g /dev/sdb1 /media/something -o force
```

---

### Post by fishmonk on 2007-12-28
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/HDD -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/HDD ntfs-3g defaults,force 0 0

I got this when I did. I tried the command line in the second choice but it said "only root can do that."

---

### Post by PmDematagoda on 2007-12-28
Post the result of:-

```
cat /etc/mtab
```

---

### Post by fishmonk on 2007-12-28
/dev/sda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sda2 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0

---

### Post by PmDematagoda on 2007-12-28
Try as given in the error message:-
```

sudo mount -t ntfs-3g /dev/sdb1 /media/something -o force
```

---

### Post by fishmonk on 2007-12-28
worked
thank you so much

---

### Post by PmDematagoda on 2007-12-28
Glad to have been able to help:).

---

### Post by xyrcncp on 2007-12-29
Hello,  I'm having mounting issues as well (I believe).  I have 7.10 with a 16GB HD.  Today I added a 160GB HD, it was previously used in a Windows PC and I formatted the drive by going to Partition Editor, unmounting it and formatting it as ext3 (I followed some instructions I found), now I can't see that drive and when I click on Properties for the drive it says it's unmounted, but there is no option to mount it.

What should I do?  Thanks.

edit:  I managed to mount it with adding Disk Mounter to the panel, and now it shows up as "disk" in the desktop and under computer as "152.7 GB Volume: disk", however, I can't modify anything in it, I can't add files or folders or anything.

---

### Post by PmDematagoda on 2007-12-29
Open Nautilus in Root mode using:-
```
gksudo nautilus
```
Then see if you can read and write to the drive.

---

### Post by LEsterFields on 2007-12-29
> **xyrcncp said:**
> Hello,  I'm having mounting issues as well (I believe).  I have 7.10 with a 16GB HD.  Today I added a 160GB HD, it was previously used in a Windows PC and I formatted the drive by going to Partition Editor, unmounting it and formatting it as ext3 (I followed some instructions I found), now I can't see that drive and when I click on Properties for the drive it says it's unmounted, but there is no option to mount it.

What should I do?  Thanks.

edit:  I managed to mount it with adding Disk Mounter to the panel, and now it shows up as "disk" in the desktop and under computer as "152.7 GB Volume: disk", however, I can't modify anything in it, I can't add files or folders or anything.

Try this

sudo chown -R user:user /media/disk

replace user with your username and disk with whichever name you chose to mount with.

---

### Post by wolfen69 on 2007-12-29
in the future, you could also plug it into a windows machine, right click it and "eject".

---

### Post by xyrcncp on 2008-01-07
> **LEsterFields said:**
> Try this

sudo chown -R user:user /media/disk

replace user with your username and disk with whichever name you chose to mount with.

It asked me for my password and then it said that my username is invalid.

> **PmDematagoda said:**
> Open Nautilus in Root mode using:-
```
gksudo nautilus
```
Then see if you can read and write to the drive.

When I do this, yes it's under Media, but I can write to it.  Do I have to do this every time I want to create something in that drive?

---

