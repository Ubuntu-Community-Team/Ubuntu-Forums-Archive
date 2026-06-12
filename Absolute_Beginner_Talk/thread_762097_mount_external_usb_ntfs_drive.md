---
title: "mount external usb ntfs drive?"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by bgiannes on 2008-04-21
I've try reading about this problem in other threads, but they are not exactly the same problem?


I have recently install Ubuntu 7.1 on a 1000Mhz old laptop with 1GRAM it's a dual boot system, run XP on the other side, (which has a ntfs partition).  All when very well, i'm liking Ubuntu very much :)

i installed ntfs-g3 and i can see and use the windows side of the disk :)

i have sony MS ready and a U3 flash drive etc etc network cards etc, all works.


..............
okay here is the problem, I have an External (37GB NTFS drive for data only) in a firewire/usb enclosure.  Which works on my other XP/W2K without problem.  But when i plug it into the laptop running ubuntu 7.1 i just a error, saying something about the drive not being ejected from XP in the wright way?

thing is it was ejected correctly!   I then try and use the "force mounting" terminal command list in the error and it doesnt work?

please help...

thanx

---

### Post by bgiannes on 2008-04-23
well, after trying to mount the drive for the 100th time, i tryed to connect the drive to one of my xp machines, XP can't connect :(  the drive was just clicking!  i then tryed pluging the drive back into the ubuntu laptop again, and it worked :) ?  I then unmounted it and plug it back into one of the XP box, ha it worked!


my only problem now is that i can't write to the drive from Ubuntu, but i can read from it.

i bet it was/is a ntfs-3g bug?

---

### Post by bumanie on 2008-04-23
Install ntfs-3g config via synaptic. After that you will have a system tools tab added to applications. Click on that and you will be able to enable read/write to an external ntfs drive.

---

### Post by bgiannes on 2008-04-28
> **bumanie said:**
> Install ntfs-3g config via synaptic. After that you will have a system tools tab added to applications. Click on that and you will be able to enable read/write to an external ntfs drive.



I did this but the drive is not always writable?

Also,  

When I use the drive with Ubuntu, and would like to go and use it on another windows pc I need to do the following:

1) un-mount it in Ubuntu

2) Re-boot the ‘Ubuntu’ laptop under XP with the drive plug

3) “eject” it, ie stop the device and unplug it.

4) Then the drive is ready for use with other windows machines.

Note:  I just can’t un-mount it and then plug it into a windows box straight up.  

It's like the drive gets tyed to the ubuntu/windows laptop, regardless which OS is running?

Is this normal, what the hay?

---

