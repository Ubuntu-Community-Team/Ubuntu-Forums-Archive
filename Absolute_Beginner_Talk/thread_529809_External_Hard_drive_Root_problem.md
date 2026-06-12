---
title: "External Hard drive Root problem"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by DaH-RaT on 2007-08-19
is there anyway i can quickly enable root to transfer a file to my external hard driver and disable root when im done? i cannot put files on it for it says i do not have permission to. i  went to properties to change it but the fields are greyed out saying "access filles" only. Any ideas?

---

### Post by Jimmyfj on 2007-08-19
sudo chown -R USERNAME:USERNAME /media/yourdrivenamehere

This will change the owner of the disk/device or you can access the drive by:

gksu nautilus - Then enter your root password and when you close nautilus the root privileges are ended and you're back to normal.

Edit - You need to run gksu nautilus in a terminal

---

### Post by DaH-RaT on 2007-08-22
man thanks dude that helped instantly :)

---

### Post by djroze on 2007-08-22
Does this cause ownership to be retained after the drive is removed/replaced?  I'm no expert, but if you're using the drive a lot, maybe it helps to modify /etc/fstab to give yourself ownership when the device is mounted...

---

