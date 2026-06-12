---
title: "How do I completely erase all data on my hard drive?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-05-15
After erasing my partitions, my hard drive still has divisions and a swap partition. I have messed up with my partition table before so I want to delete everything in my hard drive now.

How do I completely erase all data on my hard drive? 

I attached a screenshot of how GParted looks like.

---

### Post by jvc26 on 2007-05-15
Um... no attached screenshot, but with Gparted to delete EVERYTHING you would just right click, or select the partition and select 'delete partition' then it will just be registered as empty space onto which you can format to whatever format you want.
Il

---

### Post by bashologist on 2007-05-15
If you wanna securely erase your hdd so nothing can be recovered then you might wanna look at "Darik's Boot and Nuke". [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by wersdaluv on 2007-05-15
I attached the screenshot of GParted.

You can see there two unallocated blank partitions. I am wondering why those two are still divided even after I deleted my partitions and the swap partition cannot be deleted.

---

### Post by Henry Rayker on 2007-05-15
I had a similar issue...I think your swap partition may be mounted...are you running gparted on a live cd, or did you install it and run while in Ubuntu?

I would try a live cd.

EDIT: nevermind, I see that you are using a live cd. Can you choose to delete /dev/hda4? The swap resides on that partition, so that may be something you can do to get rid of the swap; if you get rid of the extended partition on which swap lives, swap will die too.

---

### Post by wersdaluv on 2007-05-15
> **Henry Rayker said:**
> nevermind, I see that you are using a live cd. Can you choose to delete /dev/hda4? The swap resides on that partition, so that may be something you can do to get rid of the swap; if you get rid of the extended partition on which swap lives, swap will die too.

I cannot delete /dev/hda4. The delete option is grayed out.

---

### Post by Henry Rayker on 2007-05-15
what options are available for both the swap and /dev/hda4 partitions?

---

### Post by wersdaluv on 2007-05-15
I managed to delete it. All I had to do was to unmount the swap partition.

Thanks guys. :)

---

