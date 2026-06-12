---
title: "usb hard drive mounted as read only, how can i change that?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by tee2 on 2006-12-05
I have a USB HDD that Ubuntu mounted for me but it mounted the drive as read-only. How do I change the permissios? From a terminal I tried "sudo nautilus" then browsing to /media where it's mounted and right-clicking and changing things but I get "Couldn't change the permissions of usbdisk-1 because it is a read-only disk."

---

### Post by igknighted on 2006-12-05
> **tee2 said:**
> I have a USB HDD that Ubuntu mounted for me but it mounted the drive as read-only. How do I change the permissios? From a terminal I tried "sudo nautilus" then browsing to /media where it's mounted and right-clicking and changing things but I get "Couldn't change the permissions of usbdisk-1 because it is a read-only disk."

What type of file system is on the disc?

---

### Post by tee2 on 2006-12-05
Ooooh it's ntfs. :-# :mrgreen:

---

### Post by MeeMaw on 2006-12-05
I just had that same problem.... I unmounted the drive and re-formatted it as a fat32 (I have XP on a separate HD I still use occasionally) If you are using only Linux you can format it diferently. Then you should be able to change the permissions.
(I, too, am a n00b.)

:-D     MeeMaw

---

### Post by Endolith on 2007-11-08
Now you can use ntfs-3g for this.  :-)

---

### Post by Harpoon on 2007-11-08
You don't need to reformat, and you should have ntfs-3g installed by default.  You do, however, want to get ntfs-config (in the repositories) and then **make sure you run it** ( a step often forgotten).  The gui is elegantly simple and will solve your problems.

---

### Post by Endolith on 2007-11-08
> **Harpoon said:**
> You don't need to reformat, and you should have ntfs-3g installed by default.  You do, however, want to get ntfs-config (in the repositories) and then **make sure you run it** ( a step often forgotten).  The gui is elegantly simple and will solve your problems.

This thread is from 2006.  :-)

---

