---
title: "Gutsy wont mount drives"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2007-12-30
Good evening
I just started my computer and Gutsy wont mount sda5 - the partition where my windows is (NTFS) and sda7 - a NTFS partition for various things. It always mounts them. What can I do? In My computer I only see the filesystem and the CD/DVD.

---

### Post by taurus on 2007-12-30
I bet if you mount either one of them by hand from a terminal, you would get a warning message about you didn't shutdown your window cleanly and you need to use the force option to mount them.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda5
sudo mount -t ntfs-3g /dev/sda5 /media/sda5
```

---

### Post by KOTAPAKA on 2007-12-30
what is this program? NTFS -3g?

---

### Post by taurus on 2007-12-30
This can explain what ntfs-3g driver is much better than I can.

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

