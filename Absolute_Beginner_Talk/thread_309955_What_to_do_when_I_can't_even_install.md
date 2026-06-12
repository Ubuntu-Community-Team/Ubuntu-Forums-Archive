---
title: "What to do when I can't even install?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2006-11-30
I've been using ubuntu 6.10 on an old laptop and I've been pretty happy with it and I wanted to install it on a PC that I'm using as a PVR with windows.  I had a problem that with version 6.10 that I couldn't install anything, because the graphics wouldn't work.  I posted a message here and it was recommended that I use ubuntu alternative.   I tried ubuntu alternative, but when it comes to partitioning my HD it gets hung up.  I have a 320 gig SATA 2.0 Western digital HD and I wanted to do a non-destructive partition the way I was able to do it on my laptop.
I also tried version 6.06 and the same results with the graphics.

I'm really not sure what to do and starting to think linux isn't ready for me yet?  I love ubuntu on my laptop, but I really wanted to use mythtv with ubuntu, instead of using windows as the PVR.

---

### Post by Ashrael on 2006-11-30
Try installing an older version of ubuntu first...you can always update later...
see how that goes...

---

### Post by nofrak on 2006-11-30
When I first installed Ubuntu, I had trouble with the partitioner as well.  Try using the most current GParted Live CD to repartition first.  It's avaliable from [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php").  
If that doesn't work, see what errors it gives you.  I ended up having to do a filesystem check on windows, and then was able to install without problems.

---

### Post by Ashrael on 2006-11-30
You tried to use the livecd first? give me a better description of your hardware, what brand/type etc... Esp. your videocard,,,

---

### Post by bone2006 on 2006-11-30
Yes I tried liveCD with 6.06 and 6.10 with results of not being able to see the screen.

With 6.10 alternative I was to start the installation, but it was hung up during the partition.

I'll give GParted newest update from the link a try.  

Thanks everybody for the quick response and below is my hardware, sorry thought it was Western digital HD, but it's actually a seagate:


Seagate Barracuda 7200.10 ST3320620AS (Perpendicular Recording Technology) 320GB 7200 RPM SATA 3.0Gb/s Hard 

ECS KN1 Lite 1.0A Socket 939 NVIDIA nForce4 Ultra ATX AMD Motherboard 

CHAINTECH SE6600/256 DDR PCI Express x16 Video Card

Hauppauge WINTV-PVR-150 PCI Interface Tuner Card

CORSAIR ValueSelect 1GB (2 x 512MB) 184-Pin DDR SDRAM DDR 400 (PC 3200) Dual Channel Kit System Memory

NEC 16X DVD±R DVD Burner Black IDE/ATAPI Model ND-3550A 

AMD Athlon 64 3500+ Venice 2.2GHz Socket 939 Processor

---

### Post by Ashrael on 2006-12-01
If I were you, i'dd strip all the hardware that's not essential out of the box and then try to install, later you can add on the other hardware..I don't think it's your videocard that's giving you a headache, I think it might be the Hauppage card.. BTW are you using a 64bit version of ubuntu??m If so, try to use 32 bit version...Keep us posted on your experiences...

---

### Post by Ashrael on 2006-12-01
Oh, i forgot to stress that it's very very very important to do the most rigorous diskcheck on all your drives before trying to install... Someone before me also said this, but failed to stress how important this was.. ;)

---

