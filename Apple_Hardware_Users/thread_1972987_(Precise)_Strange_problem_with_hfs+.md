---
title: "(Precise) Strange problem with hfs+"
date: 2012-05-04
forum: Apple Hardware Users
---

### Post by majortom67 on 2012-05-04
Hi to everybody.
12.04 should not ha ve problems reading hfs+ partitions and also writing if Journaling is disabled. Unfortunately I'm not able not work with hfs+ partitions. The error message I get is similar to: you do not have such filesystem in (...). But if I jist aplly the folllowing command:
sudo mount -t hfsplus /dev/sdc4 /mnt

wich should be only for an external disk's hfs+ partition, IT WORKS FOR ALL HFS+ partitions: they all became readable and writable.

Any idea? Any Help?

TIA
Simon

---

### Post by mode7 on 2012-05-04
I was having the same issue ([http://ubuntuforums.org/showthread.php?t=1969366](http://ubuntuforums.org/showthread.php?t=1969366)). 
I switched to standard Ubuntu (Unity) because I was frustrated with some KDE issues, that being one.

What's strange is that Nautilus can automatically mount it where Dolphin cannot. I'm not fine with using the terminal to manually mount the partition each time. I've tried all the HFS related packages to no avail.

(I don't know how Linux manages filesystems whatsoever, but "cat /proc/filesystems" did not list HFS+ on either Ubuntu or Kubuntu.)

---

### Post by majortom67 on 2012-05-04
Here is the solution:
-digit:
sudo nano /etc/modules

add the following: "hfsplus" at the end of the file.

Save and restart.
Enjoy.
Simon

---

### Post by mode7 on 2012-05-10
> **majortom67 said:**
> Here is the solution:
-digit:
sudo nano /etc/modules

add the following: "hfsplus" at the end of the file.

Save and restart.
Enjoy.
Simon
Thanks! I just tried and confirmed it worked. (Yes, I reinstalled Kubuntu after realizing I miss KDE too much :)
Such a simple fix. It annoys me that this could be nowhere to found.

---

