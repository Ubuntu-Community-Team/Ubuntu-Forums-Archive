---
title: "installing with windows xp question.."
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by elduderin00 on 2007-09-14
Hi,

I want to install unbuntu along with windows xp. I have the linux unleashed book and it says that wndows must be installed first.....So can i just intall windows as normal and then put the ubuntu disc in...boot from it and then do the partitioning with ubuntu or do i need to create a partition when i do the windows install?

Thanks!

---

### Post by skymera on 2007-09-14
mine came with windows hogging the disk.

i resized windows..IN windows. otherwise it can bugger it up.

then booted ubuntu and tada, i dual boot

---

### Post by hyper_ch on 2007-09-14
if you can, just leave unpartitioned space upon installing windows for the later use of Ubuntu.

---

### Post by anaconda on 2007-09-14
resizing windows partition to make ubuntu is just more trouble ...

and because you are planning to install both anyway, you should install windows so that it wont take the whole disk, and there will be enough unpartitioned space to install ubuntu to.
and then install ubuntu.

I have also first installed ubuntu and then windows, the only problem was that the grub (linux bootloader) needed to be re-installed after windows destroyed it.

---

### Post by elduderin00 on 2007-09-14
HI,
Thanks for the quick replies. So i should install windows so it does not take up the whole disk but not create a partition with windows....leave that until i boot from the ubuntu disc and create the partition then? just another quesiton out of interest....what happens when youve got both installed......how do you descided which OS you want to boot into? does the grub give some sort of screen on startup?

Thanks again :)

---

### Post by antoz on 2007-09-14
Yes grub gives you a screen at boot to select from. After you installed you can edit the menu.lst to select which one you want to start by default.

---

### Post by Sef on 2007-09-14
> So i should install windows so it does not take up the whole disk but not create a partition with windows....leave that until i boot from the ubuntu disc and create the partition then?

Read [Desktop Install]("http://www.psychocats.net/ubuntu/index.php").

Read [Alternate Install]("http://www.users.bigpond.net.au/hermanzone/p17.htm").

---

