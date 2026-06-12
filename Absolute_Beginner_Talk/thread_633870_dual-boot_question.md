---
title: "dual-boot question"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by saltandblues on 2007-12-07
i've never used dual boot, i've either been all windows or all linux :/

does dual booting default to one OS? in other words, if i turned the computer on and came back in three minutes would ubuntu be running (given i choose ubuntu as default)?

or do i have to specify each time i boot?

---

### Post by rsambuca on 2007-12-07
Grub can use whichever OS you want as the default.  You can also set the timeout, so that it will start booting after 2 seconds, or 200 seconds.

---

### Post by crimesaucer on 2007-12-07
But, regular default grub will choose your Ubuntu partition after like 10 or 20 second if you leave it as it is.

---

### Post by Hobbs131 on 2007-12-07
How do i go about changing these preferences?

---

### Post by Ek0nomik on 2007-12-07
> **Hobbs131 said:**
> How do i go about changing these preferences?

You need to know where both the Windows and Ubuntu partitions are.  To do this, open a terminal and type:

```
sudo fdisk -l
```

Post the output.

Or if you know what to do, edit this file:

```
sudo nano /boot/grub/menu.lst
```

Here is an example of my menu.lst:

```
title           Ubuntu 7.10, kernel 2.6.22-13-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-13-generic root=UUID=ee7c327e-72a0-42a3-9e49-816dc12917c1 ro quiet splash
initrd          /boot/initrd.img-2.6.22-13-generic
quiet

title           Steve Ballmer
root            (hd0,0)
makeactive
chainloader     +1
```

(Steve Ballmer is Windows XP)

On my box, Windows is on /dev/sda1, and Ubuntu on /dev/sda5.  As you can see in my menu.lst, you subtract 1 number.  (hd0,4) is Ubuntu, (hd0,0) is Windows.  Different naming scheme is all.

---

### Post by Duck2006 on 2007-12-07
In your menu.lst you look for the line that has,

default         0

Then change this for the entry of the OS that you want to boot from. Bye default grub in ubuntu boots ubuntu first.

---

### Post by Hobbs131 on 2007-12-07
ok thanks...it worked

---

