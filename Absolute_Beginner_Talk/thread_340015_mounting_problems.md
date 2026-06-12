---
title: "mounting problems"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by mayonesiac on 2007-01-16
hey i have a weird question:

how do i mount a hardrive with an ext3 file system when i'm using the ubuntu live cd (no ubuntu system installed on the pc). please don't ask me why i need to do this cause it's a long long story

---

### Post by taurus on 2007-01-16
Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
df -h
```
(Assuming you want to mount /dev/hda1...)

---

### Post by phr0ze on 2007-01-16
Sorry for the question but what does **df -h** do?

Thanks!

---

### Post by taurus on 2007-01-16
List all the mounted drives.

You should run it from a terminal to check out the output.  ;)

---

### Post by mayonesiac on 2007-01-16
thanks, that worked

---

