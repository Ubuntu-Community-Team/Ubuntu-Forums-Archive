---
title: "Accessing my Data drive"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by MicroChris on 2007-02-07
Hello all,

Just switched back to 6.10 from Vista.. glad to be back. 

I'm trying to access my data drive, which is an NTFS drive.

```
root@ubuntu:/# sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9587    77007546   83  Linux
/dev/hda2            9588        9964     3028252+   5  Extended
/dev/hda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        9730    78148192+   f  W95 Ext'd (LBA)
/dev/hdb5               2        9730    78148161    7  HPFS/NTFS

```

How would I add this to my fstab so I can see it, pull data off it and reformat it to Fat32? Thanks a lot.

-Chris

---

### Post by logos34 on 2007-02-07
Create a mount point:
> sudo mkdir /media/windows

then add this to fstab:
> /dev/hdb5 /media/windows ntfs nls=utf8,umask=0222 0 0

Save and close.

then
> sudo mount -a

---

### Post by bodhi.zazen on 2007-02-07
This is cool too : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by logos34 on 2007-02-07
And definitely check out that link to ntfs-config Bodhi.zazen provided above...I use it too with ntfs-3g...nice thing about it is it automatically edits your fstab for you when you change to r+w mode.  It'll save you some hassle, and the benefit of NTFS is you're not contrained by the 4GB file size limit (so things like big videos and Partimage archives will now fit!)  I've been using ntfs-3g for a short time now, and so far so good (fingers crossed)...Although just the other day I was looking through the tools in ntfsprogs and noticed one called 'ntfsfix' for repairing windows parititions in the unlikely event they are damaged by ntfs-3g...It goes on to say "You should run it **every time** after you have used the Linux NTFS driver to write to an NTFS partition in order to prevent massive data corruption from happening when Windows mounts the partition."

Sure hope that's not right, because I haven't been doing it!

---

### Post by MicroChris on 2007-02-08
Cool,

Used ntfs-3g, got the data off of it. Just reformatted it to Fat32, however.. how would I add it to my fstab as fat32?

Thanks for the help again.

-Chris

EDIT: Here's the new list

```
root@ubuntu:~# sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9587    77007546   83  Linux
/dev/hda2            9588        9964     3028252+   5  Extended
/dev/hda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9730    78156193+   5  Extended
/dev/hdb5               1        9730    78156162    b  W95 FAT32

```

---

### Post by MicroChris on 2007-02-08
Alright, I seem to have formatted, mounted, and edited my fstab correctly.

The only other question I have about this drive is: Can I make it show up when I go to Places > Computer in Gnome?

-Chris

---

### Post by logos34 on 2007-02-08
Reboot and check it again.  The drive should automount if your fstab entry is correct.

---

### Post by bodhi.zazen on 2007-02-08
> **logos34 said:**
> And definitely check out that link to ntfs-config Bodhi.zazen provided above...I use it too with ntfs-3g...nice thing about it is it automatically edits your fstab for you when you change to r+w mode.  It'll save you some hassle, and the benefit of NTFS is you're not contrained by the 4GB file size limit (so things like big videos and Partimage archives will now fit!)  I've been using ntfs-3g for a short time now, and so far so good (fingers crossed)...Although just the other day I was looking through the tools in ntfsprogs and noticed one called 'ntfsfix' for repairing windows parititions in the unlikely event they are damaged by ntfs-3g...It goes on to say "You should run it **every time** after you have used the Linux NTFS driver to write to an NTFS partition in order to prevent massive data corruption from happening when Windows mounts the partition."

Sure hope that's not right, because I haven't been doing it!

OFF TOPIC (sorry :mrgreen:)

Check out this like, it should ease some of your concerns :

[http://www.ntfs-3g.org/quality.html](http://www.ntfs-3g.org/quality.html)

---

### Post by logos34 on 2007-02-08
> Check out this like, it should ease some of your concerns :
[http://www.ntfs-3g.org/quality.html](http://www.ntfs-3g.org/quality.html)

I remember reading the first part of that page...It was one of the things that convinced me to try it because the test methods show it's anything but experimental, which is what you hear a lot. Missed the last part on how to test, though..They seem quite confident.

---

### Post by logos34 on 2007-02-08
> **MicroChris said:**
> Alright, I seem to have formatted, mounted, and edited my fstab correctly.

The only other question I have about this drive is: Can I make it show up when I go to Places > Computer in Gnome?

-Chris

So did you get it to appear?  You should see a disk icon there and on your desktop as well.

---

