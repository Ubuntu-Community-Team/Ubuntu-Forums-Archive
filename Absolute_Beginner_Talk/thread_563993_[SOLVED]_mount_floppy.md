---
title: "[SOLVED] mount floppy"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2007-09-30
Having trouble mounting floppy

I get this
$ mount /media/floppy0
mount: /dev/ is not a block device

I saw some threads about an issue with Breezy, but I am running Edgy; is the bug still there?:popcorn:

---

### Post by Waappu on 2007-09-30
Hi

see in /etc/fstab that it say fd0 not fd.

I have some problems on Edgy but can't remenber how I fix it

---

### Post by Xoanan on 2007-09-30
Didn't see that in there.
I did see this
/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5f96d011-bfe1-40a7-bc7b-37d83921e3e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=f57e4852-2844-4fef-bfb6-5283ab0549ae none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Waappu on 2007-09-30
Hi

Type in terminal```
gksudo gedit /etc/fstab
```
and change this line```
/dev/ /media/floppy0 auto rw,user,noauto 0 0
```
to```
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```
then type in terminal```
sudo mount -a
```and try mount floppy

---

### Post by Xoanan on 2007-10-01
I don't have gedit;  I am using Xubuntu.  What would I use?

---

### Post by ronald.higgins on 2007-10-01
Just use your favourite text editor, like "vi" for example.

---

### Post by alienexplorers on 2007-10-01
If youi ever have mounting problems, give this a read.
> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by Waappu on 2007-10-01
> **Xoanan said:**
> I don't have gedit;  I am using Xubuntu.  What would I use?

Use mousepad

```
gksudo mousepad /etc/fstab
```

---

### Post by Xoanan on 2007-10-01
gksudo mousepad seemed to do the trick.  Thanx:)

---

