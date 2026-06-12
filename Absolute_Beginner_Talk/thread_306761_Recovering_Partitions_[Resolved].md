---
title: "Recovering Partitions [Resolved]"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-11-25
Okay, so I did something really dumb . . .I put Ubuntu on a rather small drive (40 gigs) . . .no problems there . . .it works great and I love it. My problem is this : 
I accidentally screwed Windows XP and don't know exactly what happened . . .my dilemma is that I'm not sure I can recover the files in it that I want on Ubuntu before I do any changing . . .
This is a readout I got : mac@mac-desktop:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I know I can't mount the partition, but I'm hoping that maybe there's a way around this . . .I can't get into Windows, and I can't reinstall it because I don't have a product key anymore . . .Am I screwed, or is there an answer here? I really appreciate any help. Thanks.

---

### Post by aysiu on 2006-11-25
Are you sure you can't mount your Windows partition?

When you say you "screwed Windows XP," what exactly do you mean?

Is the data corrupted, or can you just not boot to it?

Why don't we start with tring to mount it? If that doesn't work, you can try *dd_rescue* to get the data off it.

Can you post the output of this command? ```
sudo fdisk -l
```

---

### Post by bodhi.zazen on 2006-11-25
What aysiu said :p

---

### Post by CheshireMac on 2006-11-25
~LOL~ Okay . . .by the way, thanks guys . . .so I went with the command you told me to go with . . .
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4679    37584036   83  Linux
/dev/hdb2            4680        4866     1502077+   5  Extended
/dev/hdb5            4680        4866     1502046   82  Linux swap / Solaris

How's this looking?
Also, I hope this isn't too much trouble for you guys. ~LOL~ I know my head is smashed into a million pieces right now, trying to recover this stuff . . .it's not corrupted. Windows is just stupid. ~LOL~

---

### Post by bodhi.zazen on 2006-11-25
It looks like windows is fine, just not mounted.

Try this:```
sudo mkdir /mnt/windows
sudo mount /dev/hda1 /mnt/windows
```

---

### Post by aysiu on 2006-11-25
Some slight modification to the instructions bodhi.zazen gave: ```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
```

---

### Post by CheshireMac on 2006-11-25
Now it says I don't have permission to view the contents, but it worked!! ~LOL~ Thanks a lot! Now, all I need is to change the permissions . . .I think I know how . . .but could you refresh my memory?

---

### Post by aysiu on 2006-11-25
> **CheshireMac said:**
> Now it says I don't have permission to view the contents, but it worked!! ~LOL~ Thanks a lot! Now, all I need is to change the permissions . . .I think I know how . . .but could you refresh my memory? You can't change the permissions of a Windows drive once it's mounted. You have to specify the permissions during the mounting process (stuff in **bold**)

Do this: ```
sudo umount /mnt/windows
sudo mount -t ntfs /dev/hda1 /mnt/windows **-o nls=utf8,umask=0222**
```

---

### Post by CheshireMac on 2006-11-25
You guys are involved with MENSA, right? ~LOL~ It worked . . .you guys are geniouses . . .or whatever the proper plural for Genious is. ~LOL~ Thank you so much . . .that was 60 gigs worth of data I thought I had lost forever!! You're my heroes. . .remember, when life give you lemons, you take those lemons and clone them, and make super-lemons!!!

---

### Post by aysiu on 2006-11-25
The plural of *genius* is *geniuses*.

Glad it all worked out for you.

---

### Post by bodhi.zazen on 2006-11-25
Glad to have helped. Your complements are appreciated, but I am no genius, just more experienced in Linux and willing to help :p

---

