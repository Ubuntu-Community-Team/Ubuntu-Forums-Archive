---
title: "Mount All Drives on boot-up"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Guruprasad on 2007-10-13
I want to mount all my partitions on boot-up.

How to do this?

---

### Post by taurus on 2007-10-13
You just add entries in /etc/fstab to mount them upon boot.  Post the output of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l  <-- lower case letter l, not number 1!
cat /etc/fstab
```

---

