---
title: "EXT4 corrupted, cannot fsck"
date: 2010-12-24
forum: Apple Hardware Users
---

### Post by theSuperman on 2010-12-24
My EXT4 partition is corrupted, so I cannot boot into Ubuntu. I tried using an Ubuntu Live CD but it automatically tries to mount the partition, which causes fsck (when I run it after the Live CD has booted) to say that the device is busy or exclusive or something. I cannot remember the exact message (and I am sitting at Christmas eve dinner right now). 

Trinity Rescue Kit does not recognize any of my drives on my Macbook 7,1 (I think that's the model, its the 2010), so I cannot use that. Does anyone know how to prevent Ubuntu from automatically attempting to mount drives?

---

### Post by theSuperman on 2010-12-24
So TRK apparently cannot find my partitions (or even my hard disk), but I downloaded the Gparted Live CD and booted into that. I was able to repair the filesystem that way.

---

### Post by linuxopjemac on 2010-12-26
well done!

---

