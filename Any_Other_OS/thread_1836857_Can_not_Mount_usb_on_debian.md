---
title: "Can not Mount usb on debian"
date: 2011-08-31
forum: Any Other OS
---

### Post by stamatiou on 2011-08-31
Hey guys, I have hust installed Debian but I have a problem.

Whenever I plug in a usb or external HD I take a pop up message that says
```

Error mounting: mount exited with exit code 1: helper failed with: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail  or so Debian
```What can I do?

---

### Post by Sef on 2011-08-31
Moved to Other OS Talk.

---

### Post by NightwishFan on 2011-09-01
Did you install vis usb? If so you might need to edit /etc/fstab and comment out the usb drive. First open a root terminal, then run this:
```
nano /etc/fstab
```

Find a line that looks similar to this:
```
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto     0       0
```
Add # at the beginning so it looks like this:
```
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Press CTRL+X then y to save and then reboot. Make sure you edit the right line though, post the /etc/fstab here if you are unsure.

---

