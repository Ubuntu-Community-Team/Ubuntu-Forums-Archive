---
title: "pagefile in ubuntu?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-02-05
does Ubuntu 7.10 use a pagefile or any other form of virtual memory as you would find with the Windows OS pagefile?  thanks.

---

### Post by emarkd on 2008-02-05
That's what your swap partition does.  Moving the memory paging to a separate partition really cuts down on the chances of your hard drive getting fragmented.

---

### Post by Ardrias on 2008-02-05
You have a swap partition. It's created for you automatically when you go through the installer. Are you looking to resize it or something?

---

### Post by Matt26 on 2008-02-05
no, just asking out of curiosity- but since you mention it, is resizing this partition easy to do?

---

### Post by hyper_ch on 2008-02-05
it is not difficult to partition but

(1) you could format the wrong partition if you don't pay attention (I did it once...)

(2) messing with your partition could always lead to an error --> make backups first of your important data

---

### Post by emarkd on 2008-02-05
You'd probably have to do it from a Live CD, or at least with the swap partition unmounted, but it's just a partition like any other, so it's really not bad to do.  gparted would handle it quite well, I'm sure.

---

### Post by RedRat on 2008-02-05
The size of that partition is done at installation and usually conforms to a multiple (usually 2) of your available RAM memory, e.g., 1 GB of RAM makes a partition of slightly more than 2 GB. I believe that 2 GB is the smallest partition for the swap partition but it can be made larger. You probably can make it larger but if you do decide to try, be very careful and back your system up before doing it. The resizing of any partition under any OS can be dangerous. I believe the program for doing this in Ubuntu is gpartd. Be very, very careful.

---

### Post by Liet_Kynes on 2008-02-05
Is a pagefile still really necessary? Used? Whenever i run top it always catches my attention that the swap used is always 0%

---

### Post by dgray_from_dc on 2008-02-05
> **Liet_Kynes said:**
> Is a pagefile still really necessary? Used? Whenever i run top it always catches my attention that the swap used is always 0%

It still gets lots of use on older machines with less memory.  I have a Xubuntu server with only 128Meg of RAM.  I have seen newer machines do without swap.

---

### Post by FuturePilot on 2008-02-05
Depending on the amount of RAM you have. If you have a lot of RAM you probably will rarely use swap. On my old laptop with 768MB RAM the swap gets used a lot.

---

### Post by emarkd on 2008-02-05
It also depends on what you do.  If you're editing large media files or running lots of virtual machines, that swap file gets plenty of use.

---

### Post by Ardrias on 2008-02-05
You can read more about swap going into the man pages for swapon, swapoff, mkswap. Open a terminal and type man mkswap, for instance.

You can also tweak the behaviour of swap by editing /etc/sysctl.conf and adding the line ```
vm.swappiness=XX
``` to it, where XX is a number from 00 to 100. The default in Ubuntu is 60, which you can view by typing ```
cat /proc/sys/vm/swappiness
```

The machine will need to be rebooted in order for any changes to take effect. If you have lots of ram there really is no need for the machine to swap, imo, so setting swappiness to a low value like 10 or 20 might increase performance.

---

