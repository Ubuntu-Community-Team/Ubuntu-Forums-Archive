---
title: "Another Partition size thread"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by neu_ser on 2007-10-18
I know partition size is done to death but recommended sizes seem wildly different, especially the swap.
I am completely new to linux so please bear with me.

I have approx. 50gb of a 120gb drive available for a Kubuntu install.
From what I've read I need 3 partitions: /, /home and swap.

I am just generally trying the OS and plan on installing a couple of recent games for benchmark comparison so possibly need ~10gb just for them. Does software install to / or /home? :confused:

I have 2Gb of ram and if I followed some of the replies I searched for, the swap could range anywhere from 512Mb to 4Gb.

I do not want to needlessly waste space so any advice is much appreciated.

---

### Post by juantovarm on 2007-10-18
kubuntu live cd will handle all the partitioning you need automatically, it's a pretty easy no-problems kind of task, just tell it where to install the OS and it will do everything by itself. Swap space is for smaller pc's where there's not so much memory. With 2 gigas, i don't think you'll ever use it, i have 1.5 and have never used mine. Normally programs are put in /usr/bin and the personal settings in a hidden file in /home

enjoy your experience

Juan

---

### Post by Paqman on 2007-10-18
First of all, 50GB is *tons* of room for a Linux system, so don't worry too much about getting it perfect.

When new packages get installed they go mostly into your root partition. The only thing in your /home is the preferences and settings for that user (eg: your Gnome settings like default fonts, wallpapers, etc) 

That's why 10GB is often recommended for /, it gives you plenty of spare room to install software. A fresh install is only something like 4 or 6GB, I can't remember exactly.

Swap is a funny one. With 2Gb of RAM you might not even need one. Swap is normally not used by the system providing it has enough memory.

You can always resize partitions later with Gparted if you want to adjust things (do a good back first, just in case)

---

### Post by Duck2006 on 2007-10-18
15Gb for /        "root"
1Gb swap partition
and the rest for your home partition.

---

### Post by neu_ser on 2007-10-19
Thanks for the replies people.
I am not quite there yet, Kubuntu appears to have installed ok but the bootloader is abit messed up.
I am using EasyBCD (I can't reg. on their forum as the security image will not show) and the vista bootloader to fire up grub and I'm having trouble configuring.

I've modifed part of a menu.1st to look like this:
```
title=Kunbuntu Linux 7.04
root (hd1,2)
kernel /kernel-2.6.5-gentoo?
root=/dev/hda3?
```

What would be the kernel name and what is the meaning of the last line there?

Many Thanks.

---

### Post by kolinab on 2007-10-19
neu_ser,

Just found this thread and looks like you got the partititioning advice you need. As for the GRUB question I'm willing to bet if you fire up a new thread with a descriptive subjective line someone will bite and answer the second problem in short order.

Hope you get installed OK.

K

---

