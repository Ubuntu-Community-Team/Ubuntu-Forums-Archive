---
title: "Memory errors"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by coderkind on 2007-02-04
Hi all,

I've been recommended ubuntu by a number of friends and I'm really keen to install it on my desktop at home. Thing is, I've been experiencing problems with that machine for ages now (well over a year).

I had a PC Repair guy come out before christmas who upgraded the processor and seemingly identified that the problems I was experiencing with the PC were down to the hard drive becoming corrupted (he removed that drive, leaving the other 160GB drive in). However, since I'm up-and-running again with Windows the PC still crashes now and again (especially running Firefox), and I've started the memory check from the ubuntu CD and have gotten the following after the first 10 hours or so:

[http://www.coderkind.com/errors.jpg](http://www.coderkind.com/errors.jpg)

Is it worth me continuing with trying to install ubuntu or is there a big hardware problem I need to fix beforehand (I'm guessing the latter!)? If so, any ideas where to start with trying to solve it so I can begin with ubuntu?

---

### Post by lamego on 2007-02-04
Memory is a fundamental piece of hardware and yours seem to have problems.
You should try to replace your system memory, otherwise you will get an unstable system and can possible data loss.
If you had bad memory, it was probably your only problem on the first place, not the disk...

---

### Post by coderkind on 2007-02-04
I'm just a little worried about the prospect of buying more memory and the problem existing somewhere else.

I appreciate that it only tests system memory, but what if there are other issues linked to the memory (like the memory bays themselves)? Buying more memory is going to be a waste.

---

### Post by kimpe on 2007-02-04
Yup, I'm in the same boat as you coderkind. :(  I can't install windows XP anymore and Ubuntu won't install. It's off to the 'puter store for me. I am going to just install Ubuntu and scrap Wondoze. Evloution is a wonderful thing eh!

---

### Post by deadgobby on 2007-02-04
Buy a used ram then like at 
[http://www.mcbia.com/](http://www.mcbia.com/)

Gobby

---

### Post by coderkind on 2007-02-04
Used RAM might be a possibility, although I don't know of any UK dealers off the top of my head.

It looks like a good excuse to buy another computer, which would be a good thing normally but for the fact I'm skint right now!

:(

---

### Post by shareMenaPeace on 2007-02-04
Used ram is cheap. Check 2nd Hand computers.

---

### Post by kimpe on 2007-02-04
Try this; [http://www.memorysuppliers.com](http://www.memorysuppliers.com)

---

### Post by ahaslam on 2007-02-04
Do you have an Athlon or Sempron?

I ask because the memory test regularly reports false errors on test 5/8 with standard RAM using these processors. My laptop with a Mobile Sempron also reports an error on test 5.

If you believe that the error is valid there is a 'badram' kernel patch, which will avoid allocating the faulty addresses.

Tony ;)

---

### Post by coderkind on 2007-02-05
I've an Athlon Anthony. Someone today also pointed out that the memory test may not give reliable results, and to download memtest86 instead.

I wouldn't know where to begin with a kernel patch I'm afraid; I'm still getting into the world of ubuntu!

---

### Post by az on 2007-02-05
> **coderkind said:**
> and to download memtest86 instead.


Memtest is on every Ubuntu cd.  You can run memtest by booting the live cd or the alternate cd.  It is also on an installed system.

---

### Post by kinematic on 2007-02-05
if your memory is bad i would advice to buy some kingston value ram....it's dirt cheap.

---

### Post by ahaslam on 2007-02-05
> **coderkind said:**
> I've an Athlon Anthony. Someone today also pointed out that the memory test may not give reliable results, and to download memtest86 instead.

I wouldn't know where to begin with a kernel patch I'm afraid; I'm still getting into the world of ubuntu!

I'm sure there are multiple kernel how-to's here, adding a patch of some sort is quite common & should be covered. You'll not screw anything, your current kernel will remain to fall back on. Try it, it'll cost you nothing more than a little time ;)

Please note that if you decide to replace your RAM, it'll be better to avoid budget stuff. The reason Athlons often report false errors is because they demand high quality RAM.

Tony.

---

