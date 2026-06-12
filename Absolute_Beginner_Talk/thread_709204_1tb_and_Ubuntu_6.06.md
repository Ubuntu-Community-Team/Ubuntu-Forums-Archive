---
title: "1tb and Ubuntu 6.06"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by kgls13349 on 2008-02-27
Hi people, my ubuntu 6.06 server has been running buetifully for months :) doing the job of basically just fileserver,
but i recently decided to upgrade from the puny 250gb Hdd to a 1TB hdd
Now the problem is i installed 6.06 again, mainly becouse i dont have any blank cds to burn a newer ubuntu to :roll:
the installation whent perfectly, but now it is freezing on bootup, it gets as far as saying its booting the kernal and thats it, freezes right there, im not completely sure whats wrong but im thinking maybe 6.06 cant handle 1tb sized drives?

does it handle that size of drive or not?

many thanks people :)

---

### Post by Crooksey on 2008-02-27
How is the system partitioned?

Can you post your grub.conf / menu.lst ?

---

### Post by kgls13349 on 2008-02-27
unfortunatly not, it just doesnt boot to the point where i can access or do anything,
i left the partition details as the installers default, if that helps?

---

### Post by Crooksey on 2008-02-27
Does it just freeze when loading the kernel, or does it give you any type of error message?

You can use the livecd and obtain your menu.lst.

---

### Post by kgls13349 on 2008-02-27
the last message it gives me is "uncompressing Linux...ok, Booting the kernal" and thats it does nothing more

Right i hadnt thought about the live cd :lolflag:
but then this version is the server version, doesnt have live on it, i would have to fish out my older v5 desktop disk

---

### Post by Crooksey on 2008-02-27
The server install still gives you access to a tty.

---

### Post by mrsteveman1 on 2008-02-27
Try booting with the following kernel line appended:

```
vga=normal ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off
```

If that works, remove one at a time until it stops working so you can isolate the problem.

This is quite clearly a kernel problem, if you can see it loading the kernel and then nothing, it means the kernel stopped. If it were simply not mounting root you would see that on the screen.

---

### Post by kgls13349 on 2008-02-27
its strange, i can get into the grub menu, i have three options the norml bootup, then the recovery boot and finnaly the mem test,
if i do recovery it halts and the last message oin screen is "NET: registered protocol family 2"

seems to be refering to the network adapter, yet the only thing thats changed is the hdd :confused: how can that affect the network adapter

---

### Post by halitech on 2008-02-27
this may not be related but does the motherboard support a drive of that size?

---

### Post by kgls13349 on 2008-02-27
ah, thats not something i had thought off...
but it does aknowledge it within the bios correctly, so it seems to accept it

its an epia EN15000 motherboard (nice and low power consumption and handles file serve dutys perfectly)

---

### Post by halitech on 2008-02-27
I know when I changed from my 80gig drive to the 160 that it started doing strange things, BIOS saw it fine but when booting, it would stop part way through, give a message about failing fsck and to hit CRTL-D to exit the shell. I recently reinstalled, created a bigger /boot (from 100meg to 250, not sure why I made the change) and now it boots normally. Might be something to look at.

---

### Post by mrsteveman1 on 2008-02-27
Any recent motherboard should support the drives you can get now. At most it would simply be unable to use all of the drive, but it should still show up and work for the most part.

Definitely boot the livecd and see what happens. If you can get the alternate install cd to boot, at the very least the kernel is working fine on the hardware.

---

### Post by kgls13349 on 2008-02-27
Hi,
thanks i booted the live cd, all working fine,correcty identified the hdd as 930mb

and i have got it booting uner its own power too now
after all that i found the problem was nothing to do with linux, or hardware  ](*,)

i reset the bios to the default optimised settings, changed the few settings that have to be changed, and its booting perfect now, i dont know exactly what it was hanging up on, but it was a bios setting :rolleyes:

Sorry for wasting you guys time reading and trying to help when al along it was my own stupid mistake  ](*,)


i seem to be making lots of stupid mistakes like that recently :(

Thank you for the suport, i realy appreciate it :)

---

### Post by halitech on 2008-02-27
we've all made mistakes like that : I once troubleshot a no power problem for 25 minutes before I realized the power plugs weren't plugged into the motherboard :$

---

