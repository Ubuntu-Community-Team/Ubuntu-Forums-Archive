---
title: "fstab help"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by itchanddino on 2006-11-10
I want to make sure that my harddrive is being scanned every 30 mounts in edgy as it was in dapper.  Can someone take a look at my fstab file to make sure that this is still occurring?  Thanks!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3c2858db-8d2d-4dc7-97ec-36da3c41e638 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=47f0806c-fe5b-41ee-9bb3-94e32d85ec93 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by po0f on 2006-11-10
itchanddino,

The easiest way to check would be to boot a live CD, since you can't unmount your filesystems while they are in use.  After it's booted up, open up a terminal (Applications -> Accessories -> Terminal), and type the following command:
```
$ tune2fs -l /dev/hda1 | grep interval
```

A line similar to the following should be outputted:
[FONT="Courier New"]Check interval: 30[/FONT]

[EDIT]

That is an L (ell) in the command above.  Just for clarification.

---

### Post by ciscosurfer on 2006-11-10
The [following page]("http://ubuntu.wordpress.com/?s=tune2fs&searchbutton=go%21") will help you out.

---

### Post by itchanddino on 2006-11-10
It tells me:
Check interval:                0 (<none>)

---

### Post by ciscosurfer on 2006-11-10
And did you set a new interval?  Look at the page I referenced again.

---

### Post by itchanddino on 2006-11-10
No, but on my next reboot it ran and said it was the 30th mount :)  Guess that was the wrong command.  Thanks anyway!

---

### Post by ciscosurfer on 2006-11-10
You need to add the device file to the end of the command, like this for example```
sudo tune2fs -i 1w /dev/hda2
```This will set the file system check to once a week on /dev/hda2.  To check which drive/partition you need to run it on, in a terminal as well, type```
sudo fdisk -l
```That's a lower case "L" not the number "1".
So let's say you want to fsck to run once every 60 boots on /dev/hda2, you would type in a terminal```
sudo tune2fs -c 60 /dev/hda2
```For more info, type [B]man tune2fs
[/B]To disable file system check only once for the next bootup, issue```
sudo touch /fastboot
```To force a check, issue```
sudo touch /forcefsck
```The device file names may be needed for the last two commands as well.

---

### Post by itchanddino on 2006-11-10
Yeah, it worked fine by default without all that.  Thanks though!

---

