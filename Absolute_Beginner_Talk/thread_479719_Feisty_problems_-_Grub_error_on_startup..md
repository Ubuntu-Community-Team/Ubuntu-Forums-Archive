---
title: "Feisty problems - Grub error on startup."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-06-20
OK,I reinstalled Feisty Live Desktop, downloaded the updates, turned the computer off. When I restarted I got the grub error 18 message. I put the cd back in, restarted and brought up the install screen. Didn't install, just clicked restart. I removed the cd,and by golly Feisty starts up. So now, what is happening?

I did do a sudo nano /boot/grub/menu.lst and it tells me in there that root is (hd0) 0. When I partitioned the hd I thought root went to partition (dev/hda1).

Help!!!!!!!!!!!!!!!!!!!

---

### Post by captgadget on 2007-06-20
With all the wisdom on this forum and no one can help me. Kind of strange.

---

### Post by coffeecat on 2007-06-20
Less than 2 hours and you get impatient. Tut.

(hd0,0) **is** hda1 in grub-speak.

Google 'grub manual' if you want to learn more.

---

### Post by captgadget on 2007-06-20
Don't mean to be impatient, but so often somebody has a quick response. Thanks for you info and I'll just keep checking back. If I don't turn it off then I don't have the problem.

---

### Post by dstew on 2007-06-20
Grub error 18 means that the BIOS could not access the disk cylinder that grub asked it to. This used to happen a lot when big disks were put on old motherboards with old BIOSes. The limit is about 8 Gb. The cure for this problem is to make a small /boot partition at the beginning of the disk. If you want to do that, the partition should be 100 Mb in size. Then, you need to re-install, and give the new small partition the mountpoint /boot.

It seems odd that you got that error with what seems to be a modern motherboard. Do you know if the BIOS is unusual in any way? Did you do any upgrade or downgrade of the BIOS?

---

### Post by captgadget on 2007-06-20
Is it possible to upgrade the bio by way of linux? It's a brand mother board and processor and an old 80 gig hd I had.

---

### Post by confused57 on 2007-06-20
You might first try some of the other possible solutions for grub error 18 listed in this link, before trying to update your bios:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

---

### Post by captgadget on 2007-06-20
I followed dstew's suggestion about adding the boot and everything is working just fine right now. But I didn't have to reinstall. I used gparted and resized to make the boot. Surprised me!!!

---

### Post by dstew on 2007-06-21
Great! Now I learned something new, that you don't need to re-install.

---

