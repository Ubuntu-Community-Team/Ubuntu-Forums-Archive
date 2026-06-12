---
title: "I feel stupid, can't find windows partition"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by N Clement on 2007-04-14
I feel like I just missed a memo or something.  All I want to do is be able to access the main (ntfs) windows partition from Ubuntu 6.10.  My external usb HD, which has both an ntfs and a fat32 partition is quickly mounted and accessible, so it seems that I have ntfs capabilities of some sort.

Do I need to do something with this NTFS 3G that I have heard so much about?

Thanks

---

### Post by alexlex on 2007-04-14
it sounds like you just need to mount it

---

### Post by mikewhatever on 2007-04-14
Can you post the output of
> cat /etc/fstab

---

### Post by OU812 on 2007-04-14
If you just want to access the files and folders on your ntfs partition, just look in the /media directory. If you want to write to the partition, then you will need the ntfs 3g (and fuse I think) package(s).

john

---

### Post by N Clement on 2007-04-14
yeah, so here is /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=aa8e91bc-7f5f-46c1-a319-92e8cfde9a17 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d7aafdb1-c748-4e0f-8dd0-3499d342293e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```


Ok, so I figured out how to mount it (duh!) but now I don't have access to it.
I mounted it in /windows and its access stuff is:

-x-------

I tried to change it with both:
```
chmod 211 /windows/
```
and
```
sudo chmod 211 /windows/
```

but both gave me an error that I could do it because I had a write only file system.

Does this mean that I need NTFS 3G?

---

### Post by Bushfire on 2007-04-14
If you want to write to it. You should still be able to read it; try a root session of Nautilus:

```

gksudo nautilus /windows

```

---

### Post by mikewhatever on 2007-04-14
Your Windows partition is not mounted, as you can see. It should show as /dev/sda1, assuming it is the first (C) partition.To mount it, follow this guide
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

