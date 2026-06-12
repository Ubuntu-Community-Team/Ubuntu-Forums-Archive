---
title: "unmounting from desktop"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-03-11
If I unmount a drive from desktop, how do I get it back ?
If I unmount using "unmount" command in terminal, can I just get it back with
"mount" command ?

---

### Post by dptxp on 2007-03-11
If I unmount a drive from desktop, how do I get it back ?
If I unmount using "unmount" command in terminal, can I just get it back with
"mount" command ?:guitar:

---

### Post by mrmonday on 2007-03-11
Yes. You need to know its location though. for example /dev/hda1.
```
fdisk -l
```
This will list your partitions.try:
```
man mount
```
for information on how to do it.

---

### Post by Delvien on 2007-03-11
> **dptxp said:**
> If I unmount a drive from desktop, how do I get it back ?
If I unmount using "unmount" command in terminal, can I just get it back with
"mount" command ?

for ease of use, add the applet "Disk Mounter" to your panel, makes it so easy a monkey could do it. Just left click the drive and choose the option you want.

---

### Post by dptxp on 2007-03-11
How do I add the applet ?
And will even a monkey be able to re-mount the hard-disk ?
Will other users be able to see the applet, and be able to re-mount ?
For the purpose is to keep the drive away from other users.
It is EXT3 formatted, so Windows XP (mine is dual-boot) will not
see it anyway.
:guitar:

---

### Post by bapoumba on 2007-03-11
@ dptxp: merged your other thread in here.

---

### Post by Delvien on 2007-03-11
> **dptxp said:**
> How do I add the applet ?
And will even a monkey be able to re-mount the hard-disk ?
Will other users be able to see the applet, and be able to re-mount ?
For the purpose is to keep the drive away from other users.
It is EXT3 formatted, so Windows XP (mine is dual-boot) will not
see it anyway.
:guitar:


Right click on the panel, click add applet, look for disk mounter.

Yes even a monkey can remount. Unfortunately other users will be able to remount too, if they use linux / Ubuntu, windows cannot read Ext3 if im not mistaken.

---

