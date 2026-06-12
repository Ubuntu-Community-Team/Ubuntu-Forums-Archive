---
title: "Can't unmount drive"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by opacity on 2007-11-04
I recently got Ubuntu and I found it better than windows. I installed it on a HP computer and since I still need windows for some things I didn't remove it. My Ubuntu desktop always has the Recovery drive and I can't get rid of it. Do any of you know how?

---

### Post by Pumalite on 2007-11-04
'Recovery' drive probably belongs to Windows. I wouldn't remove it if you are still using Windows.

---

### Post by opacity on 2007-11-04
I'm just trying to get it off the desktop.

---

### Post by LowSky on 2007-11-04
if you dont want it on the desktop

just unmount it, or do this

type in terminal ```
gconf-editor
``` 

then go to
 apps>nautilius>desktop

unclick volumes visible, and it wont be on yor desktop

---

### Post by opacity on 2007-11-04
I've already tried that. It doesn't appear there.

---

### Post by Pumalite on 2007-11-04
Go to Places, look in left column: you should see the partition. Right click on it and unmounted. If it doesn't work, try ind Terminal:
umount /dev/???
(??? only you know)

---

### Post by sandysandy on 2007-11-05
facing a similar problem.
how do you unmount disks on ur desktop which refuse to unmount by right clicking.

regards

---

