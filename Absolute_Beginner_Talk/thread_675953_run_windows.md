---
title: "run windows"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by joloxx on 2008-01-23
i have windows xp and recently installed linux. I now need to run my computer using windows in order to change some settings, but i am having trouble. I don't know how to start my computer in windows instead of linux.

---

### Post by maybeway36 on 2008-01-23
There should be a menu when you turn on your computer, with Ubuntu, memtest, and windows. Select windows from the list and press enter.

---

### Post by jonabyte on 2008-01-23
I have found in the past, I am not sure how this happens but, grub will only show for a second and it is easy to miss. Try pressing the down arrow key when booting your computer, after post is complete, etc.

---

### Post by joloxx on 2008-01-23
there is no option for windows in the startup screen....only memtest, ubuntu, and ubuntu recovery mode.......I know I didnt delete windows, and all of my saved data. is there another way i should be able to access running windows.

---

### Post by fatherdaly on 2008-01-23
While you were installing Ubuntu, did you make sure that you put ubuntu on a separate partition to windows, or did you let it do it for you.

Because If you let Ubuntu do it for you, it reformats the drive and installs itself, meaning no more windows

---

### Post by zhanglini on 2008-01-23
can you run Gparted and tell us what partitions you have on your hard drive?  That might show us if you have deleted XP or not.

---

### Post by bumanie on 2008-01-23
Is your computer a dual boot on a single hard drive or is xp and ubuntu on separate drives?

---

### Post by bodhi.zazen on 2008-01-23
> **zhanglini said:**
> can you run Gparted and tell us what partitions you have on your hard drive?  That might show us if you have deleted XP or not.

Or open a terminal and enter :

```
sudo fdisk -l
```

---

