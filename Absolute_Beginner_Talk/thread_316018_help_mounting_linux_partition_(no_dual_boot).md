---
title: "help mounting linux partition (no dual boot)"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by dtrizzle on 2006-12-10
Hi All,

I finally made the switch and I want to mount my large ext3 partition (hda3).  I can't figure out how to do it.  I created a folder called /media/datadisk and this is where I want to mount hda3.

1)  How do I mount hda3 to /media/datadisk?
2)  How do I make this partition mount automatically on startup?  (What exactly do I need to put in the fstab file)?

Thank you so much.  I've posted some output to assist with my questions.

Dtrizzle


```

$sudo fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2550    20482843+  83  Linux
/dev/hda2            2551        2652      819315   82  Linux swap / Solaris
/dev/hda3            2653       24321   174056242+  83  Linux
```


```
$ sudo mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hdc on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=dorian)
tmpfs on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw,mode=0755)


```

---

### Post by ginkhao on 2006-12-10
Sounds like you are almost there

Everything you need to know is here:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Basically edit your /etc/fstab file and add this to the end:

```
/dev/hda3 /media/datadisk ext3 defaults 0 0
```

Then do a "sudo mount -a" and see if it is mounted.

If it is correctly mounted at this point then it should automatically mount at startup.

Check the permissions, you may need to adjust them, the article above shows you how.

---

### Post by bscbrit on 2006-12-10
To mount the drive manually, type

sudo mount -t ext3 /dev/hda3 /media/datadisk

To mount it in fstab

/dev/hda3 /media/datadisk ext3 defaults 0 0


EDIT : ginkhao types faster than I do!

---

### Post by dtrizzle on 2006-12-10
Thank you both for the quick reply.  I'm getting an error message.  I do not know what that means.  Any ideas?

```
$ sudo mount -t ext3 /dev/hda3 /media/datadisk

mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Dtrizzle

---

### Post by slimer on 2006-12-10
Have you formatted you partition?

---

### Post by dtrizzle on 2006-12-10
I have not.  I'll google how to do that and post the result.

---

### Post by slimer on 2006-12-10
mke2fs -j /dev/hda3 - will format you partition in to ext3

---

### Post by dtrizzle on 2006-12-10
Thank you so much.  All is working now.  I'm windoz free and proud of it.  I just have to figure out how to use this OS.  I can tell with the community support, it won't be very hard.  Thanks again.

Dtrizzle

---

### Post by slimer on 2006-12-10
Good luck dude!

---

### Post by floke on 2006-12-10
You won't regret it!

Enjoy:-D

---

