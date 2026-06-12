---
title: "USB devices not detected after bootup..."
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by jarvis13 on 2007-03-05
Ok. When I boot up with a USB device (Ipod, mouse etc) plugged in already, it reads them just fine. However, if I plug them in AFTER I boot up, it won't detect them. Not so much a major problem, but it's getting annoying.

Any quick fix for this?

---

### Post by oilchangeguy on 2007-03-05
not sure, but ubuntu may not offer hot swap, as windows does.

---

### Post by jarvis13 on 2007-03-05
It worked in Kubuntu Feisty Herd 4, but when I decided to switch back to gnome and got herd 5, it no longer works (Switched via clean install, not update)

---

### Post by jarvis13 on 2007-03-07
anybody?

---

### Post by superm1 on 2007-03-07
When you say that they aren't read, as in they don't get power?  Or as in the OS doesn't work with them.  I'm assuming the latter, in which case you need to check dmesg and lsusb.  Dmesg will tell you kernel messages related.  lsusb will show all usb devices currently being recognized.

---

