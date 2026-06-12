---
title: "Permissions"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by afterburner on 2007-04-20
Hi, 

Im just wondering...whats up with not being able to copy and paste files into the usb key, and floppys? I need to transfer some files, and i get an error message saying i dont have permission to do this...what do i do to get this permission, or to work around this issue?

Thanks

---

### Post by taurus on 2007-04-20
Press <Alt>F2 and type

```
gksudo nautilus
```
Now, you can copy whatever to wherever you want so be careful with that.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by markl187ld on 2007-04-20
What file system is the USB key formatted with?

---

### Post by Pobega on 2007-04-20
Make sure you have the option "user" for the specific device in /etc/fstab, for example if your drive shows up at /dev/sdb1, /etc/fstab should have:

> /dev/sdb1       /media/thumbdrive           vfat    user,noauto        0       0

Or something similar to that. Edit it how you need, save and try again.

---

### Post by afterburner on 2007-04-20
Thanks.

I didnt that, and the window opened up...i then copy the desired file, and then open another directory in the same window (usb key), but the paste function is now gone...what do i do now?

Oh, its FAT32

---

