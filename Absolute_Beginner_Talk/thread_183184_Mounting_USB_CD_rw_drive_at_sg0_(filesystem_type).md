---
title: "Mounting USB CD r/w drive at sg0 (filesystem type)?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Steff_DK on 2006-05-27
When I try to mount my USB CD R/W drive with this command:
```
sudo mount /dev/sr0 /media/cdrom0
```
it mounts a read-only.

When I open gnomebaker I can see in the error that it expects to find the CD-RW at dev/sg0 but when I try to mount it with:
```
sudo mount /dev/sg0 /media/cdrom0
```
It wants the filesystem type. I tried mount -a and mount -t iso9660(or whatever it was) with no luck.

Any suggestions?

---

### Post by Sutekh on 2006-05-27
Try mounting it with extra options

Check out the man page for more info
```
man mount
``` [Mount Man Page]("http://www.die.net/doc/linux/man/man8/mount.8.html")


I don't know if you have any other CD drives, but it might be less confusing to create a new mount folder for the CDRW (/media/cdrw is just an example, it can be whatever you wish)
```

sudo mkdir /media/cdrw
sudo mount /dev/sg0 /media/cdrom0 - t iso9660 **-o rw**
``` OR

You can edit your /etc/fstab so that you can mount it in an easier way, and also automount (should work)

This code makes a copy of the file before editing
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` When the editor opens, you should add a line like this
```
/dev/sg0    /media/cdrw    udf,iso9660    rw,user,noauto    0    0
``` Again if /media/cdrw is where you want to mount the CDRW drive.

Then you can save the file with Ctrl+O and exit with Ctrl+X.

Then to mount the drive, use```
mount /dev/sg0
``` The **user** option allows an ordinary user to mount (no need for sudo).

---

### Post by Steff_DK on 2006-05-28
Tried:
```
sudo mount /dev/sg0 /media/cdrom0 -t iso9660 -o -rw
```
And got:
```
mount: /dev/sg0 is not a block device
```

:confused: 

(there was a blank CD media in the CDRW at the time - does that matter?)

---

### Post by Sutekh on 2006-05-28
Can you confirm that the CD is really /dev/sg0?

What is the output from this command, which will list the available partitions
```
sudo fdisk -l
```

---

### Post by Steff_DK on 2006-05-28
sudo fdisk -l gives:
```
Disk /dev/hda: 15.1 GB, 15103033344 bytes
255 heads, 63 sectors/track, 1836 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1790    14378143+  83  Linux
/dev/hda2            1791        1836      369495    5  Extended
/dev/hda5            1791        1836      369463+  82  Linux swap / Solaris
```

There are no other drives or partitions on the laptop, than the 15gb harddrive ...

---

### Post by Sutekh on 2006-05-28
That was with the blank disc?  What about the output with a used CD in there?

How about using this command
```
tail -f /var/log/messages
```
Then plug in the USB CD drive.  What new messages appear?

---

