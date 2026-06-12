---
title: "iso mount is fstab"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by milanvora2 on 2008-04-13
Hi, 
I'm trying to enter an entry in fstab to mount an iso file at startup.

File located in /home/milan
Filename: TE3700data.iso
Mount point: /media/cd1

Entry in fstab is: /home/milan/TE3700Data.iso /media/cd1 iso9660 ro,loop=/dev/loop# 0 0 

But it doesn't work.
Does anyone know what I'm doing wrong.
Thanks
Milan

---

### Post by sisco311 on 2008-04-13
Try:
/home/milan/TE3700Data.iso /media/cd1 iso9660 ro,loop 0 0

---

### Post by milanvora2 on 2008-04-13
I tried, but it still didn't work.

---

### Post by llamakc on 2008-04-13
> 
/home/milan/TE3700Data.iso /media/cd1 iso9660 ro,loop,auto 0 0


Should work.

---

### Post by milanvora2 on 2008-04-15
Thanks it finally worked.
I had forgottent o create the mount location directory and that's why it kept failing.
Thanks for the help

---

