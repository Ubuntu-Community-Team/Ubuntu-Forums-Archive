---
title: "resizing partition with knoppix"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by onearmedpanda on 2008-02-16
i am booting to knoppix so i can resize a partition that's taking up my whole hard drive and make a new one out of the remaining space. when i open gtparted, and right click it, i see the resize option but its ghosted and i can't click it. the linux swap on the other hand can be resized, but i want to resize the other one. it says its status is active, i don't know if that is bad, i tried to unmount the partition but it says its already unmounted. any suggestions on why i can't resize it? thanks in advance

---

### Post by gn2 on 2008-02-16
If you are using Gparted in a booted session, if the partition you want to edit is mounted, you must unmount it.
If the partition contains / then Gparted Live CD is the tool for the job, it's very simple to use.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

