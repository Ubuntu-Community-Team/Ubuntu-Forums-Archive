---
title: "NTFS  unmounting problems"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by dave724 on 2007-06-07
I have a usb2 drive formatted in ntfs file system. I can read and write to the drive, but when I go to eject it it say's writing to drive and unable to unmount. Even after it finishes to write it can not unmount. I have to go to an win xp machine and stop access that way I can remount the next time I use the drive. What can I do to solve this?

---

### Post by matthewboh on 2007-06-08
All you need to do is to go into a file browser (Places)  and select the USB drive, right click and select "Unmount".

---

### Post by dstew on 2007-06-08
If you are trying to unmount using the command line, remember the command is **umount**, and not unmount.

---

### Post by veerakumar on 2007-06-08
Linux Kernel has only limited NTFS write support.
Your problem may be associated with it.
It can only write to pre-existing files of same size only.

---

### Post by Inxsible on 2007-06-08
you should use pmount and pumount for all external drives and usb sticks. They will mount the drive automatically under /media.

---

