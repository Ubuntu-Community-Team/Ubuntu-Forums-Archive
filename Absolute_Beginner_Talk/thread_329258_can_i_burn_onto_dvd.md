---
title: "can i burn onto dvd?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by will954 on 2007-01-01
can i burn ubunto onto a blank dvd? im out of normal cds

---

### Post by mikewhatever on 2007-01-01
Other then a waste of space on the DVD ,I don't see why not. I still have Ubuntu 5.10 on a DVD.

Good luck.

---

### Post by will954 on 2007-01-01
glad it works. i dont mind using a blank dvd as i have quite a lot.

instead of making a new topic does anyone have a good link telling me how to partition my hard drive and dual boot? ive heard about partition magic but i just want to be sure

---

### Post by Nda on 2007-01-01
I'm assuming you want to dual-boot with Windows, in which case I recommend this guide: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/).

I have found it to be accurate and comprehensive and suggest reading as much of it as you can before installing Ubuntu so that you understand what you are doing and why.

Nda

---

### Post by tagra123 on 2007-01-01
> **will954 said:**
> glad it works. i dont mind using a blank dvd as i have quite a lot.

instead of making a new topic does anyone have a good link telling me how to partition my hard drive and dual boot? ive heard about partition magic but i just want to be sure

Boot the live CD

Under the System-Administration-Menu is GPARTED

Gparted can resize the partition for you.

For ubuntu and windows I usually use something like this

20-40 GB for windows (NTFS) if you plan on loading a lot of games go with the higher number.
10 GB for the root partition of UBUNTU  ( Normally I just leave this as free space and let ubuntu make the root and swap from this - I specify the already formatted home on the list of screens during the install process - manual selection)
20-40 for the ubuntu HOME folder 
BALANCE OF FREE SPACE AS A FAT 32 partition (I called min linwinshare)

I moved my my documents folder to the linwinshare partition it came up as "J:" on my computer. I just open my document and select properties and then moved it to the ne drive.  Basically by having the fat32 partition it makes it easy to share data although there is a driver for windows that will allow ext2/3 partitions to be used directly from windows. If you use ext2/3 you wont need t mess with defragmenting.

---

### Post by rbhigday on 2007-01-01
> **will954 said:**
> can i burn ubunto onto a blank dvd? im out of normal cds

Burned my copy of Ubuntu a few days ago onto a dvd disk with no problems, Used the dvd twice now to install Ubuntu. Like someone said just a waste of space and a few extra cents more but hey I had no cdrom at the time either. :D

---

### Post by will954 on 2007-01-01
well ive got the live distro working an i am impressed. much better looking in my opinion then knoppix or slax. is there any way to get the screen resolution to 1280x1024? its saying the highest is 1024 x 768

edit

i have a 320gb hard drive. how much should i partition for linux? also on ubuntu under system there is an instal option. if i have made a partition should i install with that?

---

