---
title: "Few questions"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Evilchicken on 2005-12-07
I installed 5.04 Hoary Hedgehog last night because XP crashed beyond repair and I needed a good reason to switch. Im lking ubuntu its pretty nice but I have a few problems.

First, when I was creating partitions I made my primary 20.2 gigs and my logical .3gigs. Whenever im logged in I cant write to the primary partition. I want to be able to use that space! Is this a permission problem? Am I not the root user?

Next, how on earth do you install XMMS? My linux machine doesnt have an internet connection so I transfer stuff via a flash drive. I downloaded XMMS and unzipped it but cannot figure out how to install it! Please help.

Last, how do you install any program :confused: I cant figure it out!

Thanks for your help.

---

### Post by Pablo_Escobar on 2005-12-07
Installation :
> sudo dpkg -i packagename.deb but without the net it'll be kind of hard because of the dependencies (other needed packages).

---

### Post by Evilchicken on 2005-12-07
does anyone know how to fix the primary partition jizz?

---

### Post by aysiu on 2005-12-07
What's the primary partition? NTFS? FAT32? Ext3?

By the way, [XMMS has quite a few dependencies](http://packages.ubuntu.com/breezy/sound/xmms).

I would work on getting that internet connection up, even if it's just dial-up.

---

