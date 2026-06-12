---
title: "problem mounting external usb hard drive"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-03-26
Im having problem mounting my 320gb external usb hard drive. yesterday before i went over to a buddy the disk was odly emty, saying that the disk was only around 100gb in use and only 50gb free. I didnt think much about it but over at my buddy the disk showed that there was 200gb+ emty. we transfered 180gb of data to it. But now when im put it in my computer again the disk wont show up ](*,) 
I did "sudo fdisk -l" but the disk seems to have not been regoniced.

what do i do?

---

### Post by eljalill on 2007-03-26
You can look at what it's called in gparted, and then do
sudo fdisk -l /dev/name to make sure, it's not there .
In gparted you can also see, whether it recognises the file system.

---

### Post by U5tabil on 2007-03-26
> **U5tabil said:**
> Im having problem mounting my 320gb external usb hard drive. yesterday before i went over to a buddy the disk was odly emty, saying that the disk was only around 100gb in use and only 50gb free. I didnt think much about it but over at my buddy the disk showed that there was 200gb+ emty. we transfered 180gb of data to it. But now when im put it in my computer again the disk wont show up ](*,) 
I did "sudo fdisk -l" but the disk seems to have not been regoniced.

what do i do?

Strange enough the disk showed up after a complete restart of the computer...

---

### Post by eljalill on 2007-03-26
One thing I sure learned in my time with Linux is,
that rebooting can do miracles. :)

---

