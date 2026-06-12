---
title: "MacBook Air kernel scheduling for ssd's"
date: 2008-07-15
forum: Apple Hardware Users
---

### Post by stream303 on 2008-07-15
After playing with an Asus eeepc that uses SSD's instead of spinning mechanical hard-disks, there is the suggestion in other forums to change the kernel's default io-scheduling from CFQ to DEADLINE when using ssd disks.  I would think this would benefit the MacBook Air as well.

You can see which scheduler your kernel is using with:

```
cat /sys/block/sda/queue/scheduler
```

(Substitute sda with whatever your system uses)

There is a way to change it on the fly, but I forgot to take notes on that. :)

To make the change permanent, you can edit your /boot/grub/menu.lst and add

```
elevator=deadline
```

to the end of your kernel lines in menu.lst

It provided a nice boost to my ssd-based mini laptop running Mandriva, so I wonder if anyone has experimented with the MacBook Air with this..

---

