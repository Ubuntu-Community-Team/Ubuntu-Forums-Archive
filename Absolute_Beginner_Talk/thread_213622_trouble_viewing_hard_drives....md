---
title: "trouble viewing hard drives..."
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by iamthez on 2006-07-11
Hi guys, I just installed Ubuntu as a dual boot with Widows XP.There are three hard drives, but I can only view the contents of the drive that Ubuntu is installed on.

Whenever I try to view the other two (in root mode and in normal) I get this error: 

```

**Unable to mount the selected volume.**
error: device /dev/hdb1 is not removable
error: could not execute pmount
```


On a side note, Windows XP detects the hard drive (says so in the device manager) but won't let me access it.

Do any of you know how to fix either of these problems?

---

### Post by wombat20 on 2006-07-11
> **iamthez said:**
> 
On a side note, Windows XP detects the hard drive (says so in the device manager) but won't let me access it.

Do any of you know how to fix either of these problems?

The following will allow you to access Linux drives from within Windows (so it says, never tried it).
[http://www.fs-driver.org/](http://www.fs-driver.org/)

In the other direction, I'm having similar trouble, but not worrying about it too much as I only use XP for games (all it's good for, IMO).

---

### Post by majed on 2006-07-11
I dual-boot and all is fine here...

Look at these:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")
[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

Good luck!

Majed

---

### Post by steve.horsley on 2006-07-11
These notes should help...

[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

### Post by stig on 2006-07-11
> **wombat20 said:**
> The following will allow you to access Linux drives from within Windows (so it says, never tried it).
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Anyone know if there is a Windows 98 version?

---

### Post by iamthez on 2006-07-11
thanks... its all working, basically :D

---

