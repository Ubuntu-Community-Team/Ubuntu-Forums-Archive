---
title: "mbt gone...."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by elmo541992 on 2007-08-05
so i got a book from the library called "linux desktop hacks"  the first thing there is, is telling you to erase and rewrite the mbt. well, for some reason, the mbt didnt rewrite correctly, and i now have no mbt.  is there anyway i can recreate this???  i have all of my files on there, and i was going to back it up in about a week, and the last back up doest have much (5 months old).

---

### Post by dreadlord_chris on 2007-08-05
The mbt?
What exactly did you do?

---

### Post by jfinkels on 2007-08-05
You want the Windows boot table, or GRUB?

---

### Post by elmo541992 on 2007-08-05
i'd perfer grub

---

### Post by jfinkels on 2007-08-05
> **elmo541992 said:**
> i'd perfer grub

You'd *prefer* GRUB, or do you *need* GRUB? What was it before?

If you install Ubuntu, GRUB will automatically be installed on the hard disk on which you choose to install Ubuntu.

If you want to install JUST grub, try Super GRUB Disk: [http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)

---

### Post by elmo541992 on 2007-08-05
i eraced the first 512b of the drive.

---

### Post by elmo541992 on 2007-08-05
i'm trying super grub now

---

### Post by Nekiruhs on 2007-08-05
> **dreadlord_chris said:**
> The mbt?
What exactly did you do?
I believe he/she means MBR (Master Boot Record).

---

### Post by elmo541992 on 2007-08-12
sorry it took me so long to respond.  anyway.. using a different grub loader won't work...  the partition table is gone too.  is there any way I can get this back???

---

### Post by adrian15 on 2007-08-17
> **elmo541992 said:**
> sorry it took me so long to respond.  anyway.. using a different grub loader won't work...  the partition table is gone too.  is there any way I can get this back???

If you want to regenerate your partition table try to use the gpart command or the testdisk program from a live cd such as system rescue cd or maybe get a dos floppy image with testdisk in it.

adrian15

---

