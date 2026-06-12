---
title: "What if i don't want a partition..."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by 127.0.0.1 on 2007-08-18
Hi, this is my first post and i come here with not a real problem. it just a case of GRUB not doing what i want it to do. 

here's the deal: i do not want to partition my hard drive. what i want instead is to install ubuntu (festive fawn 7.04) on an external hard disk, and have the partition on the external as well. instead, when i installed Ubuntu, it installed Ubuntu on my external, and GRUB and the partition on my internal primary hard drive. now, when i boot it lunches dural boot and i have to select an OS before i can get on with my daliy computing, witch isn't a problem, unless you have parents that don't like new stuff, that they are not used to on the computer they paid $1000+ for... if i don't have my external hard disk pluged into my USB ports i will get a GRUB error21.

What i am asking is, how can (if it is posible) i put the partition and GRUB on my external HDD and be able to auto boot windows with out having to go through dural boot. OR if that isn't posible, how can i at least put windows xp at the top of the dural boot list?

Thanks.

---

### Post by arsenic23 on 2007-08-18
This is how I do it.  ( Note: You'll need your external drive to be eSATA. ):

On my one machine that still has a Windows install on it I have the two drives for the NTFS raid plugged into my sata 02 and 03 ports, and then I have an eSATA port plugged into my sata 00 slot.  In this way, if I boot my machine with the external drive turned on, then it boots into Grub.  If not then it just ignores 00 and 01 and boots into the raid.  I love having it setup like this because I can dual boot and still have grub set to 0 seconds.

---

### Post by Zalbor on 2007-08-18
I haven't tried, but I assume that when it asks you to partition you can choose the external drive, and when it asks to install grub you can just install it on the external drive as well. Does that not work?

---

### Post by arsenic23 on 2007-08-18
Well, I supose if your machine can boot from USB ( asuming this is a USB drive ), then it might work if you set your bios up to boot from USB before it trys the hard drive.

---

