---
title: "Partition on re-install"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Jugney on 2007-12-26
Hey group,

First of all, I love all you posters out there who have helped me and are helping everybody out there with their problems. This is one of the reasons Ubuntu ROCKS!

A week ago I installed Ubuntu on my laptop as a dual boot with Vista. I used Vista's Shrink Volume command (as many dual boot guides recommend ) and set 20GB aside as "Unallocated Space" (Windows term) for Ubuntu's use.

Now a week later, I want to install the 64 bit version and also give Ubuntu all the free space not needed for Vista. I went back into Vista's partition tool and re-expanded the main C: volume, effectively overwriting my previous Ubuntu install - including the boot folder. Oops. Now my system won't boot off anything other than a CD.

My question is, when I'm in the Ubuntu installer, will there be a way to safely partition a space for Ubuntu while keeping my Vista files intact? 

I'm sorry if this seems like an obvious question, but last time I shrunk C and created "Unallocated space" to install Ubuntu on to. This time I didn't do that, so the C drive is just a wide open plane. I defragmented it a couple times to prepare for the install, so my files are not all over the place. But is the installer smart enough to let me create a new partition without overwriting any of my Windows files?

Thank you for any help,
Jugney

---

### Post by autocrosser on 2007-12-26
In a short word---Yes  If you look at the installer on the LiveCd, it will give you several options---use complete disk, use available free space & manual partitioning.

easiest to to go with option #2

---

### Post by estin on 2007-12-26
a similar problem happened to me a while back when i was still doing the dual boot thing.  i just booted with the cd and re-installed ubuntu.  the installation partition manager let me resize my hdd again and i re-installed ubuntu.  the grub boot loader was fixed and my windows xp partition was untouched.  hope that answers your questions, i just switched to ubuntu exclusively so i'm also a little green at this.  LOL

---

### Post by Jugney on 2007-12-26
Will this also work on the text installer? 

The Live CD does not work for me. THe screen simply goes blank after loading the drivers and the hard driev LED on my laptop stops doing anything. I suspect it has something to do with my nVidia graphics card, as Ubuntu itself didn't work until I installed the nVidia restricted drivers.

Jugney

---

### Post by LaRoza on 2007-12-26
> **Jugney said:**
> Will this also work on the text installer? 

The Live CD does not work for me. THe screen simply goes blank after loading the drivers and the hard driev LED on my laptop stops doing anything. I suspect it has something to do with my nVidia graphics card, as Ubuntu itself didn't work until I installed the nVidia restricted drivers.

Jugney

You can shrink the partition in the text installer. 

With the new Ubuntu, you can alter the partitions of Vista.

If you want to have more control, you can use the GParted Live CD, the latest version works fine with Vista.

---

### Post by Jugney on 2007-12-26
Thanks. I will go with the installer partitioner.

Jugney

---

### Post by LaRoza on 2007-12-26
> **Jugney said:**
> Thanks. I will go with the installer partitioner.

Jugney

That works fine too.

---

### Post by Jugney on 2007-12-26
[Message removed by user]

---

