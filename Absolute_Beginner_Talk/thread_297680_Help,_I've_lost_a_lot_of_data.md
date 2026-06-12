---
title: "Help, I've lost a lot of data"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-11-11
Hi,
I have a machine with two drives in it. I mounted the second one to a directory in my file system called Shared. I moved a bunch of data into it. Now the data is gone. Is possible that the system just lost the mount point, or did I really lose all my data?

Will

---

### Post by loclei on 2006-11-11
i guess you could see if the data is lost in two ways
1  try to mount that drive again like you mounted it the first time
2  take the drive that you think has data loss and put it in a different pc and you'll see either in dos or in windows if your data is there or not

---

### Post by gantww on 2006-11-11
It looks like it didn't remount after I rebooted. I have to reboot so rarely that I just freaked out for a minute. How do I mount the drive again in a way that makes it automatically do it at startup?

---

### Post by bodhi.zazen on 2006-11-11
you haev to add an entry in [fstab](http://ubuntuforums.org/showthread.php?t=283131)

What is you mount command and I'll give you the line for fstab.

---

### Post by gantww on 2006-11-11
I honestly don't remember how I did. It's been months.

The drive is the second one in the system and was formatted with whatever the default is for Ubuntu. It should be mounting into the /Shared directory.

It looks like the fstab file got altered by the update to Edgy.

---

### Post by bodhi.zazen on 2006-11-11
> **gantww said:**
> I honestly don't remember how I did. It's been months.

The drive is the second one in the system and was formatted with whatever the default is for Ubuntu. It should be mounting into the /Shared directory.

It looks like the fstab file got altered by the update to Edgy.

LOL it is not hard.

What is the output of ```
sudo fdisk -l
```
_Note_: That is a small "L".

Which partition do you want to mount?

---

### Post by gantww on 2006-11-11
wgant@sauron:~$ sudo fdisk -l

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7169    57584961   83  Linux
/dev/hda2            7170        7476     2465977+   5  Extended
/dev/hda5            7170        7476     2465946   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    7  HPFS/NTFS

---

### Post by gantww on 2006-11-11
The 80 Gig drive is the one that seems to be missing.

---

### Post by taurus on 2006-11-11
> **gantww said:**
> wgant@sauron:~$ sudo fdisk -l

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7169    57584961   83  Linux
/dev/hda2            7170        7476     2465977+   5  Extended
/dev/hda5            7170        7476     2465946   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    7  HPFS/NTFS

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

And if you plan to write to NTFS, better install ntfs-3g first...

---

### Post by gantww on 2006-11-11
This is the first I had noticed about it being formatted as NTFS. It started out that way back when in was a Win2K server, but I distinctly remember reformatting.

---

### Post by bodhi.zazen on 2006-11-11
Try:
```
sudo mkdir /mnt/Shared
sudo mount /dev/hdb1 /mnt/Shared -t ntfs
```

If you need the partition mounted ro, add this to fstab:

```
/dev/hdb1 /mnt/Shared ntfs auto 0 0
```

If you need rw, do you recall did you use ntfs-3g ?

---

### Post by gantww on 2006-11-11
OK,
I installed ntfs-3g. Now what do I do?

---

### Post by bodhi.zazen on 2006-11-11
If it is  not ntfs, what is it? ext3, reiserFS, ?

In that case use auto:

```
sudo mount /dev/hdb1 /mnt/Shared
```

And for fstab:```
/dev/hdb1 /mnt/Shared auto auto,users 0 0
```

Setting permissions depends on the file system.

---

### Post by bodhi.zazen on 2006-11-11
> **gantww said:**
> OK,
I installed ntfs-3g. Now what do I do?

mount....

for ntfs-3g

sudo mount /dev/hdb1 /mnt/Shared -t ntfs-3g -o users,rw

---

### Post by gantww on 2006-11-11
Ok, it's mounted now.

Now I just have to make it permanent. Here's what the fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=5b2bc9b0-313b-4379-85d3-e33d4223f72e / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=cc46c7ad-4976-4fa7-bc6d-8f168af8f57e none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by bodhi.zazen on 2006-11-11
> **gantww said:**
> Ok, it's mounted now.

Now I just have to make it permanent. Here's what the fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=5b2bc9b0-313b-4379-85d3-e33d4223f72e / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=cc46c7ad-4976-4fa7-bc6d-8f168af8f57e none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

So it is ntfs?

/dev/hdb1 /mnt/Shared ntfs-3g auto,users,umask=000 0 0

---

### Post by gantww on 2006-11-11
Apparently so. I don't want it to be though. I'm pulling all the data off of it now. I'm going to go to something else. Any particular format you would suggest?

---

### Post by bodhi.zazen on 2006-11-11
> **gantww said:**
> Apparently so. I don't want it to be though. I'm pulling all the data off of it now. I'm going to go to something else. Any particular format you would suggest?

I currently use ext3 (I am conservative that way). I have been looking at jfs and xfs. I am concerned with reports of massive data loss with xfs in the event of power outages, althouh I may be paranoid....

---

### Post by bodhi.zazen on 2006-11-11
Before you get too far....

type mount in a terminal to see what type fo FS your partition is....

```
mount
```

It is possible fdisk is mis-identifying the partition ? ?

---

### Post by gantww on 2006-11-11
Everything is reading off of there correctly. I'm even transferring MP3s from it to my Windows machine and they even play. So I imagine that I probably screwed up when I was formatting the drive.

---

