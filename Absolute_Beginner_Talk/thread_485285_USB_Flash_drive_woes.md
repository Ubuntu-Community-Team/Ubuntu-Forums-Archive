---
title: "USB Flash drive woes"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by DBGOTD on 2007-06-26
I changed some of the settings on my usb flash drive to get read/write capabilities but skillfully disabled it by accident, ha. Now when I try to mount it it says 
"Unable to mount volume [nameofusbdrive]"
Details:
"mount_point cannot contain the following charactersL newline, G_DIR_Separator (usually /)"
I understand what the details message is saying I think, but I don't know how to change my mount point so that I stop having this problem!

---

### Post by kpkeerthi on 2007-06-26
```
I changed some of the settings on my usb flash drive to get read/write capabilities
```

You mean... you edited /etc/fstab? Can you post the contents of fstab?

---

### Post by DBGOTD on 2007-06-26
> **kpkeerthi said:**
> ```
I changed some of the settings on my usb flash drive to get read/write capabilities
```

You mean... you edited /etc/fstab? Can you post the contents of fstab?

No, actually I went to properties -> drive -> settings and changed the information in there. But it was a few days ago and I don't remember precisely what I wrote (ha) and I can't access the drive to find out what I wrote either.

But here's my /etc/fstab anyways

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=cbf98141-1967-450e-aecb-7960db7097b5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=ba5ac856-9a0c-4efc-9656-0855eb2b368b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
```

---

### Post by DBGOTD on 2007-06-26
:-(

---

### Post by kpkeerthi on 2007-06-26
Plugin your USB drive and see if it is getting displayed in Places -> Computer. Right click the drive-> Properties -> Volume Tab -> Remove the mount point setting. Unplug the drive and plug it in back

---

