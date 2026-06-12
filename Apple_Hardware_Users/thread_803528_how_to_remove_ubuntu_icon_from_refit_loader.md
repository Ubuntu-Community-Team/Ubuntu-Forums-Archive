---
title: "how to remove ubuntu icon from refit loader?"
date: 2008-05-22
forum: Apple Hardware Users
---

### Post by beemzet on 2008-05-22
Hi guys. I have installed ubuntu on macbook pro recently. But whenever the computer starts I got this refit window where three icons show up: mac, ubuntu, ubuntu. I want to delete one ubuntu icon (since I have only one ubuntu installed).

What I did to install was:
1. installed refit;
2. partitioned my HDD using bootcamp;
3. booted from livecd (ubuntu) and deleted the partition and chose to install on the biggest free space;
4. after installation i did the following:
      sudo grub
      find /boot/grub/stage1     // i got hd0,2
      root (hd0,2)
      setup (hd0)     //(according to another manual, i did setup (hd0,2))
      quit
5. Rebooted and entered to ubuntu through both icons, both work fine.
6. Now I have this two ubuntu icons on the refit load window. When I tried "find /boot/grub/stage1", and "find /boot/grub/stage2" both give (hd0,2).

My question is how can I delete one of the ubuntu icons?
Thank you all.

---

### Post by cyberdork33 on 2008-05-22
> **beemzet said:**
> My question is how can I delete one of the ubuntu icons?
Thank you all.
the problem is that you have installed the stage 1 loader to two locations on your disk, and refit sees both of them. You need to clear the bootcode from one location. There was a thread posted just awhile ago with several suggestions:
[http://ubuntuforums.org/showthread.php?t=800698](http://ubuntuforums.org/showthread.php?t=800698)

---

### Post by beemzet on 2008-05-22
thanx a lot

---

