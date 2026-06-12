---
title: "Card Reader"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by ya-manickill on 2008-03-05
Hey, I have just bought a combi 3-port usb-hub and 15-in-1 card reader.

I plugged on one of my SD cards and it said "Unable to mount the device"

Upon clicking "Details" it said "mount: /dev/sde1: cannot read superblock" Origionally it told me that it was read only and so I changed the permissions for that.

I have 5 SD cards...and my 512 MB and 64 MB ones work fine. However, my 3 2GB ones all have this error. Could it be something to do with the size?

---

### Post by herbster on 2008-03-05
Plug the cards in and paste the output of:

```
ls -la /media
```

---

### Post by ya-manickill on 2008-03-05
```
total 84
drwxrwxrwx 12 root root  4096 2008-03-05 23:45 .
drwxr-xr-x 22 root root  4096 2007-12-20 19:30 ..
lrwxrwxrwx  1 root root     6 2007-08-26 16:16 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 cdrom0
drwx------  2 root root  4096 2008-03-05 13:34 disk
drwx------ 10 ali  root  8192 1970-01-01 01:00 disk-1
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 Docs
-rw-r--r--  1 root root  1344 2008-03-05 19:43 .hal-mtab
-rw-------  1 root root     0 2008-03-05 13:34 .hal-mtab-lock
drwxr-xr-x  2 root root  4096 2007-08-29 15:17 hda3
drwx------  9 ali  root 32768 1970-01-01 01:00 My Book
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 PCLOS
drwxr-xr-x  3 root root  4096 2007-12-15 19:12 usbdisk
drwxr-xr-x  3 root root  4096 2007-12-15 19:13 usdisk
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 Windows
```



disk-1 is my usb pen
My Book is my HDD
so I assume disk must be the card.

---

### Post by ya-manickill on 2008-03-05
When I plug one of my working ones in, I get this.

```
total 100
drwxrwxrwx 13 root root  4096 2008-03-05 23:51 .
drwxr-xr-x 22 root root  4096 2007-12-20 19:30 ..
lrwxrwxrwx  1 root root     6 2007-08-26 16:16 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 cdrom0
drwx------  2 root root  4096 2008-03-05 13:34 disk
drwx------ 10 ali  root  8192 1970-01-01 01:00 disk-1
drwx------ 10 ali  root 16384 1970-01-01 01:00 disk-2
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 Docs
-rw-r--r--  1 root root  1446 2008-03-05 23:51 .hal-mtab
-rw-------  1 root root     0 2008-03-05 13:34 .hal-mtab-lock
drwxr-xr-x  2 root root  4096 2007-08-29 15:17 hda3
drwx------  9 ali  root 32768 1970-01-01 01:00 My Book
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 PCLOS
drwxr-xr-x  3 root root  4096 2007-12-15 19:12 usbdisk
drwxr-xr-x  3 root root  4096 2007-12-15 19:13 usdisk
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 Windows

```

---

### Post by herbster on 2008-03-05
First off, have you had them in a Windows machine and removed them without clicking "Safely remove" ??

Is /media/disk the one that's not being read? It appears the ones being read (disk-1,disk-2 and My Book, are they working fine?) are readable by you and the others are root only.

---

### Post by ya-manickill on 2008-03-06
It shouldn't show up should it? Because it isn't mounted. It isn't disk...that's changed now.

```
total 84
drwxrwxrwx 12 root root  4096 2008-03-06 19:15 .
drwxr-xr-x 22 root root  4096 2007-12-20 19:30 ..
lrwxrwxrwx  1 root root     6 2007-08-26 16:16 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 cdrom0
drwx------ 10 ali  root  8192 1970-01-01 01:00 disk
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 Docs
-rw-r--r--  1 root root  1174 2008-03-06 19:15 .hal-mtab
-rw-------  1 root root     0 2008-03-06 19:15 .hal-mtab-lock
drwxr-xr-x  2 root root  4096 2007-08-29 15:17 hda3
drwx------  9 ali  root 32768 1970-01-01 01:00 My Book
drwxr-xr-x 22 root root  4096 2008-03-04 10:46 PCLOS
drwx------  2 ali  ali   4096 2008-03-05 23:59 .Trash-ali
drwxr-xr-x  3 root root  4096 2007-12-15 19:12 usbdisk
drwxr-xr-x  3 root root  4096 2007-12-15 19:13 usdisk
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 Windows
```

Is what I get with or without the card in.

---

### Post by herbster on 2008-03-06
usbdisk and usdisk are both owned by root. That's probably the issue. Put the card in and paste the output of

```
df -h
```

and

```
ls -la /media
```

again.

---

### Post by steveneddy on 2008-03-06
> **herbster said:**
> First off, have you had them in a Windows machine and removed them without clicking "Safely remove" ??



Funny that I read this.

My daughter who is in University came down this weekend and I was trying to get some pics off of her SD card via my card reader in the lappie.

I wouldn't read it or acknowledge the card.

I keep a USB card reader in my mobile case just for these occasions & it worked OK then.

I put another card in the lappie later that night & it read it, but the second card is one of mine that I know has been ejected properly from a Linux box.

I guess my daughter isn't ejecting it or something.

That is all. :D

---

### Post by jerrynewt on 2008-03-06
Don't mean to jump the thread but I'm having the same problem with my ScanDisk. Output of ls -la /media is
total 20
drwxr-xr-x  5 root root 4096 2008-03-06 17:29 .
drwxr-xr-x 21 root root 4096 2007-11-08 23:32 ..
lrwxrwxrwx  1 root root    6 2007-11-08 23:11 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-11-08 23:11 cdrom0
-rw-r--r--  1 root root    0 2008-03-06 17:29 .hal-mtab
drwxr-xr-x  2 root root 4096 2008-02-10 18:34 ScanDisk
drwxr-xr-x  2 root root 4096 2007-11-08 23:11 sda1

so the card is being recognized but doesn't show up under Places>My computer at all.
Output of df -h is
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              19G  2.9G   15G  17% /
varrun                379M  112K  379M   1% /var/run
varlock               379M  4.0K  379M   1% /var/lock
udev                  379M   88K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   34M  345M   9% /lib/modules/2.6.22-14-generic/volatile
/dev/sda6              34G  8.6G   24G  27% /home

Any ideas ?? thanks and pardon the jump.

---

### Post by herbster on 2008-03-06
steveneddy, Yep, I had some headaches with various SD cards and external drives a while ago and read up fairly extensively on the permissions/accessbility of these drives in linux/Windows. From what I understand, it's the "locking" of the device and hogging of permissions in a manner of speak that Windows has a nasty habit of.

jerrynewt, Can you paste the output of

```
sudo fdisk -l
```

with the device plugged in, of course.

Also, which filesystem is your ScanDisk? NTFS, FAT, EXT3, etc.? I don't want to advise altering permissions before knowing this.

---

### Post by jerrynewt on 2008-03-06
Yes output of sudo fdisk -l is
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3719    29872836   83  Linux
/dev/sda2            7440        9871    19535040   83  Linux
/dev/sda3            9872       14593    37929465    5  Extended
/dev/sda4            3720        7439    29880900   83  Linux
/dev/sda5           14312       14593     2265133+  82  Linux swap / Solaris
/dev/sda6            9872       14311    35664237   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 257 MB, 257425408 bytes
65 heads, 32 sectors/track, 241 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         242      251376    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(249, 64, 32) logical=(241, 46, 32)

This is with the card inserted.

---

### Post by jerrynewt on 2008-03-06
By the way this is on my Toshiba Satellite Pro 6100 laptop --dual boot Gutsy and Hardy Alpha 5 -- 120 gig hd-768 gig ram-Pent 4 processor.

---

### Post by jerrynewt on 2008-03-06
bump

---

### Post by herbster on 2008-03-06
Looks like your external drive is FAT32 and is owned by root. You can try this:

```
sudo chown user:user /media/ScanDisk
```

Replace "user" with your username in both instances. Then unmount the drive, mount it back and see if you can access it.

---

### Post by jerrynewt on 2008-03-07
Tried it herbster and still will not mount.

---

### Post by herbster on 2008-03-07
Okay, plug your drive in and give the output of:

```
sudo mount /dev/sdb1
```

---

### Post by jerrynewt on 2008-03-07
When I have my Lexar flash drive mounted at the same time as the ScanDisk the output is

mount: /dev/sdb1 already mounted or /media/SECURE II busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/SECURE II

When I unmount the flash drive the output is

mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

---

### Post by ya-manickill on 2008-03-07
**fdisk -l**

```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf5aa

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         316        1012     5598652+  83  Linux
/dev/hda2            1927        4864    23599485    5  Extended
/dev/hda3               1         315     2530206    b  W95 FAT32
/dev/hda4            1013        1926     7341705   83  Linux
/dev/hda5            4591        4864     2200873+  82  Linux swap / Solaris
/dev/hda6            1928        4590    21390516   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    c  W95 FAT32 (LBA)

Disk /dev/sdb: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7624     1951728    6  FAT16
Note: sector size is 1024 (not 512)

Disk /dev/sdf: 2059 MB, 2059403264 bytes
38 heads, 37 sectors/track, 1430 cylinders
Units = cylinders of 1406 * 1024 = 1439744 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        2861     4022029    6  FAT16

```

It is /dev/sdf1

**ls -la /media**

```
total 84
drwxrwxrwx 12 root root  4096 2008-03-07 13:34 .
drwxr-xr-x 22 root root  4096 2007-12-20 19:30 ..
lrwxrwxrwx  1 root root     6 2007-08-26 16:16 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 cdrom0
drwx------ 10 ali  root  8192 1970-01-01 01:00 disk
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 Docs
-rw-r--r--  1 root root  1180 2008-03-07 13:22 .hal-mtab
-rw-------  1 root root     0 2008-03-07 13:22 .hal-mtab-lock
drwxr-xr-x  2 root root  4096 2007-08-29 15:17 hda3
drwx------  9 ali  root 32768 1970-01-01 01:00 My Book
drwxr-xr-x 22 root root  4096 2008-03-04 10:46 PCLOS
drwx------  2 ali  ali   4096 2008-03-05 23:59 .Trash-ali
drwxr-xr-x  3 root root  4096 2007-12-15 19:12 usbdisk
drwxr-xr-x  3 root root  4096 2007-12-15 19:13 usdisk
drwxr-xr-x  2 root root  4096 2007-08-26 16:16 Windows

```

**df -h**
```
Filesystem            Size  Used Avail Use% Mounted on
varrun                601M  100K  601M   1% /var/run
varlock               601M     0  601M   0% /var/lock
udev                  601M  136K  601M   1% /dev
devshm                601M     0  601M   0% /dev/shm
lrm                   601M   34M  567M   6% /lib/modules/2.6.22-14-generic/volatile
/dev/hda6              21G  7.8G   13G  39% /home
/dev/hda1             5.3G  2.0G  3.1G  39% /media/PCLOS
/dev/sdb1             1.9G  1.9G   23M  99% /media/disk
/dev/sda1             299G   58G  241G  20% /media/My Book
```

---

### Post by jerrynewt on 2008-03-07
I have the Secure II and the ScanDisk inserted at the same time now and this is the outuput of ls -la /media

total 26
drwxr-xr-x  6 root      root 4096 2008-03-07 11:29 .
drwxr-xr-x 21 root      root 4096 2007-11-08 23:32 ..
lrwxrwxrwx  1 root      root    6 2007-11-08 23:11 cdrom -> cdrom0
drwxr-xr-x  2 root      root 4096 2007-11-08 23:11 cdrom0
-rw-r--r--  1 root      root    0 2008-03-07 10:31 .hal-mtab
-rw-------  1 root      root    0 2008-03-07 11:28 .hal-mtab-lock
drwxr-xr-x  2 jerrynewt root 4096 2008-02-10 18:34 ScanDisk
drwxr-xr-x  2 root      root 4096 2007-11-08 23:11 sda1
drwx------ 14 jerrynewt root 6144 1969-12-31 18:00 SECURE II

And this is output of df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              19G  3.0G   15G  17% /
varrun                379M  116K  379M   1% /var/run
varlock               379M  4.0K  379M   1% /var/lock
udev                  379M  100K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   34M  345M   9% /lib/modules/2.6.22-14-generic/volatile
/dev/sda6              34G  8.3G   24G  26% /home

The Secure II flash drive mounts just fine and shows up on my desktop, and I can umount it just fine. The ScanDisk does not show up on the desktop or under Places>Computer at all. Any mor help would be appreciated very much. Been trying to get this to mount forever and still no luck. Thanks again.

---

### Post by herbster on 2008-03-07
Jerrynewt, is the ScanDisk FAT32? Which filesystem is that one? If it is, you can try

```
sudo chmod 777 /media/ScanDisk
```

And try unmounting/remounting it again.

---

### Post by herbster on 2008-03-07
Ya-manickill, try:

```
sudo mkdir /media/card
sudo chown user:user /media/card
sudo chmod 777 /media/card
sudo mount /dev/sdf1 /media/card
```

With "user:user" being your username in both cases.

That has got to mount your doggone card, I've had many little SD cards and even the biggest pains in the butt got going with those permissions.

---

### Post by jerrynewt on 2008-03-07
Ok herbster tried it and this is what I got

jerrynewt@Jerry2:~$ sudo mkdir /media/ScanDisk
mkdir: cannot create directory `/media/ScanDisk': File exists
jerrynewt@Jerry2:~$ sudo chown jerrynewt:jerrynewt /media/ScanDisk
jerrynewt@Jerry2:~$ sudo chmod 777 /media/ScanDisk
jerrynewt@Jerry2:~$ sudo mount /dev/sdf1 /media/ScanDisk
mount: special device /dev/sdf1 does not exist

This is with the Secure II flash drive inserted at the same time as the ScanDisk. I get the same results with the flash drive removed and only the ScanDisk inserted.

---

### Post by jerrynewt on 2008-03-07
bump

---

### Post by herbster on 2008-03-07
Okay, just to clear it up for me, are you using a multi-card reader device or are you talking about two separate devices, like an SD card AND a hard drive? This should be easy to get going but I'm in about a dozen threads right now and a bit befuddled, don't want to go down the wrong path out of confusion. Lemme know.

---

### Post by craig-tx on 2008-03-08
Don't want to hijack the thread, but I'm in the same boat.

For me I'm trying to mount a 1 GB Memory Stick Micro (M2).  I am using a multi-card reader that installs in one drive bay and connects to a USB header.

> 
Disk /dev/sdf: 997 MB, 997195776 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00050aa3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         121      971901    b  W95 FAT32

craig@bubs:/media$ sudo mount /dev/sdf1 /media/m2/
mount: special device /dev/sdf1 does not exist


The curious thing:  gparted recognizes the card and can reformat it, but it is still not mountable.  I have reformatted the card using both FAT16 and FAT32.

I am now seeing that I also can't mount ANY of my SD cards.  I never seemed to have a problem with those in the past.  Was there a recent update that could have cause these issues?

EDIT:
The Plot Thickens...  It is now looking like it may be my card reader.  I pulled out an older USB HUB/Card reader and it will read both my SD cards and my M2 card.  Now I need to figure out if it's a software issue (driver, etc.) or hardware issue.

---

### Post by jerrynewt on 2008-03-08
I think by jumping this thread I am just adding to your confusion -- lol!!
Ya-manickill I believe  is using the multi card reader. I just have the sd card plugged into the card reader slot on the laptop, and the Lexar jumpdrive plugged into the usb port.

---

### Post by ya-manickill on 2008-03-10
I tried that, but when I get to the mounting stage, I got the same error

mount: /dev/sde1: can't read superblock

I don't know why...and this is starting to annoy me.

---

### Post by ya-manickill on 2008-03-10
I am using a multi-card reader as well.

It is Belkin (Ultimate Connectivity) combi 3-port usb hub and 15-in-1 card reader.

Thanks for trying

---

### Post by ya-manickill on 2008-03-17
bump

---

### Post by craig-tx on 2008-03-25
Well, I decided to look into it again.  I booted the PC with the Live CD.  I remember that the drives worked in the past when I ran the live CD.  This time, they didn't.  So I assume it's a hardware issue.

I decided to do one more thing.  As I mentioned before, the problematic card reader in my case connected to a USB header on my motherboard.  I decided to swap it to a different header, and IT WORKED.  Ok so I would guess then that the header is bad, but I plugged in the front USB ports to that header and they both work as well.

So basically for me, swapping the card reader and front USB header cables fixed my problems.

The question I have now is WHY???  I wish I had swapped them back to see if I could re-create the problem.  Or if just moving the cable corrected a bad contact (and nothing on my machine is more than 3 months old, so I know the contacts are clean...)

---

### Post by ya-manickill on 2008-04-22
I have decided that the card reader that I bought can't handle 2GB SD cards. Because some readers and stuff can't. So I think I'm giving up on it.

Thanks for all your help guys.

---

