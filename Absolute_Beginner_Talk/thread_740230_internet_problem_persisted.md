---
title: "internet problem persisted"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by T2manner on 2008-03-30
okay.
i was having some trouble with my internet problem with my wireless usb adapters and installing the drivers and what not.
i finally got it to work, but then my ubuntu got super slow so i reinstalled ubuntu.
i was followed the directions here [http://ubuntuforums.org/showthread.php?t=713544&page=4](http://ubuntuforums.org/showthread.php?t=713544&page=4)
and the last thing i did was

> Just look at the /etc/modprobe.d/blacklist file with the text editor:
Code:

gksudo gedit /etc/modprobe.d/blacklist

If there is nothing in the file, add the line blacklist p54usb, save the file, and reboot.

except i added > #interferes with ndiswrapper
blacklist p54usb instead and now my usb adapter doesn't even work on ubuntu!!

---

### Post by T2manner on 2008-03-30
Bump

---

### Post by T2manner on 2008-03-30
:confused::confused::confused:

---

