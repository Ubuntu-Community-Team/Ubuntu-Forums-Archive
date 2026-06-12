---
title: "External HD no longer recognized"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by ltg01 on 2007-06-30
Here's another External HD question for the knowledgable:

I had my Maxtor 300gb external drive hooked up, auto-mount all good to go,   Installed the NTFS configuration tool to aide with the write/rewrite issue..  I keep all my media on my drive, aptly named 'Saria'.  Output of fdisk:

$ fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36483   293049666    7  HPFS/NTFS
------

Then I attempt to mount:

$ sudo mount /dev/sda /media/Saria
mount: you must specify the filesystem type

$ sudo mount -t ntfs /dev/sda /media/Saria
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
---

I change to mount /dev/sda1, and it mounts, but I can not access the folder or files, so I'm a disaster right now.

It all stemmed from me plugging my drive into my girlfriend's computer (har har) so she can access my files.  Any ideas?

---

### Post by drowner on 2007-06-30
What happens when you try to mount it is sda1? Cause thats the way to do it.

you say it mounts... but what is the actual problem?

---

### Post by ltg01 on 2007-07-01
I do not have the permissions to read/write, or view the files in the folder.

If I use the desktop environment, and click to the folder, it has a small red X in the upper right corner, and will not allow me to open either.  But yes, it mounts just fine

---

