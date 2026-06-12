---
title: "how do i mount a fat32 file system"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-02-09
how do i mount hda1 it is formated as fat 32,
i know how to do most of it but dont know how to put it in fstab.i tried

                       ```
/dev/hda1    /media/shared    fat32   defaults  0    1
```

but that did not work as fat32 is not a recognised file system

here is my fstab.


Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       24321   195358401    b  W95 FAT32

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9602    77128033+  83  Linux
/dev/hdb2            9603       10011     3285292+   5  Extended
/dev/hdb5            9603       10011     3285261   82  Linux swap / Solaris
rex@rex-desktop:~$


thank you

---

### Post by jonger on 2007-02-09
i'm a quasi-noob but,

try replacing fat32 with vfat in fstab.

cheers,
jon

---

### Post by mvaniersel on 2007-02-09
I think the correct filesystem is not fat32 but vfat. See also "man 8 mount" and "man fstab"

edit: beaten :(

---

### Post by nalioth on 2007-02-09
Here is a nice script that works.

[http://ca.geocities.com/ic56@rogers.com/65/diskmounter-latest.txt](http://ca.geocities.com/ic56@rogers.com/65/diskmounter-latest.txt)

You may have to get it from the google [cache](http://64.233.167.104/search?q=cache:zzYaJlTxioYJ:ca.geocities.com/ic56%40rogers.com/65/diskmounter-latest.txt+diskmounter&hl=en&ct=clnk&cd=9&gl=us), but it's the same version.

---

### Post by STREETURCHINE on 2007-02-09
thanks all for your replies.after an extensive search through the forums i found the solution


:lolflag:

---

### Post by po0f on 2007-02-09
STREETURCHINE,

You should post a link to the thread that helped you just in case someone stumbles across this thread first.

---

### Post by STREETURCHINE on 2007-02-09
> **po0f said:**
> STREETURCHINE,

You should post a link to the thread that helped you just in case someone stumbles across this thread first.

thanks,

yes i was going to ,but as i am busy loading ubuntu on to 3 machines and windows on to 2 outhers,i am a little pushed for time so here is the solution.

Edit /etc/fstab

Code:

gksudo gedit /etc/fstab

and add this line to the end of it.

Code:

/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0

Save it. Now, create a new mount point and mount it.

Code:

sudo mkdir /media/hda1 
sudo umount /dev/hda1
 sudo mount -a 
df -h

ps ..as posted by taurus :)

---

