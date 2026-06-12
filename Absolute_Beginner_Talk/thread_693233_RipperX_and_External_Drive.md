---
title: "RipperX and External Drive"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by GayRockies on 2008-02-10
I'm not sure if I still qualify as an "absolute beginner", but I still feel that way with Linux most days.

In any case, I've been using RipperX to rip CD's to .mp3 with great results on two computers.  However, I have one laptop (well, portable desktop - the damned thing weighs 14 lbs) that I like to use for this purpose.  I typically use an external USB drive to rip discs, expecially when I'm doing a lot of them, because I like to put the wear and tear on the (cheaper) external drive.

However, RipperX will not recognize the external drive.  It wants me to use the internal one.  Does anyone know if there's a way to get it to recognize this drive?

Kind regards,

M.J.

---

### Post by RebounD11 on 2008-02-10
if you can see it within the storage devices or if it shows up with lsusb (I'm assuming it is on a USB connection) you can try mounting it manually (when you insert a disc):

```
sudo mount /dev/sdXY /media/cdrom2
```

where sdXY is the name of the device (e.g. sda1 - in my case is the root partition) and
you can replace /media/cdrom2 with whatever mount point you like

---

