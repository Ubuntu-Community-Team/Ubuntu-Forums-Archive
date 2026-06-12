---
title: "formatting hdd.."
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-01-17
what program can i use to format a hard drive on linux.

---

### Post by npmeyer on 2006-01-17
GParted works great for both partitioning and formatting hard drives.  To get it, issue

```
sudo apt-get install gparted
``` 
or get it through Synaptic.

If you don't need to partition the hard drive and just want to format it, you can use System > Administration > Disks.

---

### Post by Sef on 2006-01-17
If you want or need to partition the hard drive, you must use Breezy Live CD,  another Live CD or partitioner that is on a CD
.

---

### Post by npmeyer on 2006-01-18
I thought you could use gparted to partition a second, unmounted hard drive.  The question wasn't clear, but I guess I made a bad assumption about what it was asking.

---

### Post by grim918 on 2006-01-18
i tried to use gparted but it wont let me delete or change the partitions that are already on the hdd. i want to get rid of some old windows partitions. does anyone know how i can get rid of the partitions or is there no way to get rid of them.

---

### Post by dueY on 2006-01-18
[QUOTE=grim918]i tried to use gparted but it wont let me delete or change the partitions that are already on the hdd. i want to get rid of some old windows partitions. does anyone know how i can get rid of the partitions or is there no way to get rid of them.[/QUOTE]

If you have the Windows CD I believe you could boot with that and format to unallocated space from there.

---

