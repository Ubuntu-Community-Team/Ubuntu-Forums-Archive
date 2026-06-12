---
title: "re-install grub on macbook"
date: 2008-01-26
forum: Apple Intel Users
---

### Post by furious105 on 2008-01-26
Hi...
I've install ubuntu 7.10 on a macbook's partition. After I've resize the ubuntu's partition and when I reboot the macbook and select (with refit) the ubuntu installation, grub don't start.

How can i fix or reinstall grub without reinstall ubuntu?

Thanks, bye :)

---

### Post by cyberdork33 on 2008-01-26
see the "multi-boot mactel" how-to linked in my signature.

---

### Post by furious105 on 2008-01-27
> **cyberdork33 said:**
> see the "multi-boot mactel" how-to linked in my signature.

Thanks, but i've already try that method, and it doesn't work because the partition's table is change...:(

---

### Post by cyberdork33 on 2008-01-27
> **furious105 said:**
> Thanks, but i've already try that method, and it doesn't work because the partition's table is change...:(
I don't know what you mean by that. You need to sync the tables (in refit) if it has changed.

---

### Post by furious105 on 2008-01-27
> **cyberdork33 said:**
> I don't know what you mean by that. You need to sync the tables (in refit) if it has changed.

I'm sorry...but I don't speak english wery well :)

I have a 80Gb hard disk in my macbook... I've create 2 partitions : the first of 69Gb for the osx and 5Gb for ubuntu.

Yesterday while I installed eclipse the space was finish; than I've decided to add 2 gb to the ubuntu partition's. (I've resized osx's partition with disc utility in osx, and than I've add the free space to the ubuntu's partition from a live ubuntu cd)
After the reboot I've select ubuntu in refit, and grub doesn't start.

Now I try to re-install grub in ubuntu's partition, but it doesn't work.

can yuo help me?
 thanks bye :D

p.s I don't have a swap partition and I use ubuntu 7.10 AMD64

---

### Post by cyberdork33 on 2008-01-27
You can install grub to the MBR if you are only dual-booting. It won't hurt anything. If it still doesn't work, you may have other problems from resizing your Ubuntu partition.

---

