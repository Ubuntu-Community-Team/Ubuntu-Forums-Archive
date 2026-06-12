---
title: "external hard drive issues"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by shinigami414 on 2006-08-16
i'm new to linux.i have a western digital external hard drive that i use with my windows laptop. i want to use it with my linux computer but my xfce4 desktop doesn't recognize it. it worked when i had the default ubuntu desktop on, but my computer is so old that it needs the xfce to run faster. i've been trying to find info on how to get it to work and it seems that i need to mount the hard drive, but i have no clue how to do that. any help would be great. thanks.

---

### Post by anaconda on 2006-08-17
If it worked with ubuntu then it should also work with xubuntu. here is how you can mount it:

sudo su
mkdir /external
mount -t auto /dev/sda1 /external

now you should be able to access your hd in /external -folder

This is if your main hd is IDE.. if your main hd is a SATA drive, then change sda1 to sdb1, and if you have 2 SATA disks then change sda1 to sdc1..etc..

---

### Post by Bloch on 2006-08-17
Sorry

---

