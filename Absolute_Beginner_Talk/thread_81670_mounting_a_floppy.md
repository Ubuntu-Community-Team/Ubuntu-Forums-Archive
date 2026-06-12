---
title: "mounting a floppy"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by blueberrycheesecake on 2005-10-24
i tried to open a floppy but this showed up.

acolyte@ds9:~$ mount /media/floppy0
mount: I could not determine the filesystem type, and none was specified

so i edited fstab:mad:

acolyte@ds9:~$ sudo gedit /etc/fstab

and changed the line

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

to ...

/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

why couldn't ubuntu recognize the filesystem type when its in auto?

---

### Post by Jussi Kukkonen on 2005-10-25
[edit: fixed a bad wording]

mount uses heuristics (not understandable by mere humans) to select which fs type to use, and if that fails, it tries those listed in */etc/filesystems* or, if that does not exist, */proc/filesystems*...

Hoary seems to not have /etc/filesystems, so it uses /proc/filesystems, which does not contain vfat. **I think** You could create /etc/filesystems with 
```
sudo cp /proc/filesystems /etc/filesystems
```
and add vfat there, but I've never done that, and don't know the specifics...

---

### Post by BatsotO on 2005-10-25
I think there's nothing wrong with fstab.
I think the command should be look this :
mount /dev/fd0

/media/floppy0 is the destination where /dev/fd0 mounted. 

For simplicity you can add disk mounter to your panel. You can install MToolsFM, it's enable you to browse the disk without having to mount it.

---

### Post by tray02 on 2005-10-25
try mnt (yeah, ignore me, I don't know what I'm doing) :P

---

### Post by mapman on 2005-10-25
I had the exact same problem, then changed the fstab to use vfat for the floppy.  And it fixed the problem.  Worked fine in hoary....wonder why the change:confused:

---

