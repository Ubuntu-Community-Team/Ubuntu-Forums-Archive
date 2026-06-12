---
title: "resizing my linux partitions"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-10-20
my home partition is running out of space, and my root (/) has a lot free. How can i resize the partitions to give more to /home?
My gparted doesn't allow me to. I guess is an authorization thing

---

### Post by Pumalite on 2007-10-20
You need to use the Gparted Live CD. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by kellemes on 2007-10-20
> **Pulka said:**
> my home partition is running out of space, and my root (/) has a lot free. How can i resize the partitions to give more to /home?
My gparted doesn't allow me to. I guess is an authorization thing

You need to do this from the Linux-livecd or dedicated gparted-environment.. like [Gparted-livecd]("http://gparted.sourceforge.net/livecd.php")
The thing is.. in order to resize the partitions they need to be **un**mounted, not possible from a working system that's depending on these mounted partitions.

---

### Post by Pulka on 2007-10-20
> **kellemes said:**
> 
The thing is.. in order to resize the partitions they need to be **un**mounted, not possible from a working system that's depending on these mounted partitions.

meaning...not possible?

---

### Post by ayenack on 2007-10-20
Use a LiveCD or[ GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") as the guys above suggested. Look on the GParted web site for instructions.

---

### Post by Pumalite on 2007-10-20
The Live CD does not mount the drive/partitions at boot.

---

### Post by ayenack on 2007-10-20
If you use the Ubuntu Live CD you'll need to go to System>Administration>Partition Editor from there you'll be able to edit your partitions.

---

