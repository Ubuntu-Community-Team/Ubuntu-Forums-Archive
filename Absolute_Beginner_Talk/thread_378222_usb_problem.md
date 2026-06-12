---
title: "usb problem"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by nwadams on 2007-03-07
hi

i'm a complete newbie and dont know very many commands yet...
i have no usb when i use ubuntu...none, my usb mouse doesn't even work...please help

thanks in advance

---

### Post by superm1 on 2007-03-07
Well for starters, are your usb ports providing power?
If you have an optical mouse, is it lighting up?

Next, you can check Device Manager to see if your USB card is listed.

System->Administration-> Device Manager

---

### Post by nwadams on 2007-03-07
no, no power what so ever, and they work fine with windows

i have an amd athlon 64 3000+
msi rs480 motherboard
geforce 7600gs
1gb ram

---

### Post by captain crash on 2007-03-08
> **nwadams said:**
> no, no power what so ever, and they work fine with windows

i have an amd athlon 64 3000+
msi rs480 motherboard
geforce 7600gs
1gb ram


I have the exact issue on a similar setup. No light on the USB, no power and no USB devices work at all. Funny, my USB worked fine in 'live' mode because I clicked on the Install Link on the desktop with my USB mouse.

I have an Athlon 64 3700
some P.O.S. ECS motherboard
GeForce 6600GT
and 1 GB Ram as well

This is not a hardware issue because USB works on XP, Fedora and previous Ubuntu installs.

---

### Post by superm1 on 2007-03-08
Do you guys see any errors loading usb modules in 
```
dmesg
```
?

---

### Post by captain crash on 2007-03-10
> **nwadams said:**
> hi

i'm a complete newbie and dont know very many commands yet...
i have no usb when i use ubuntu...none, my usb mouse doesn't even work...please help

thanks in advance

Try turning off your USB Legacy Support in your BIOS. I had the same problem and it worked for me. Best of luck.

---

### Post by wheels. on 2007-03-10
turning off USB legacy support did not work for me :( 
still stuck with no mouse

---

### Post by nwadams on 2007-03-11
thanks, i'll try turning off legacy usb support
may i ask what effect that will have on my windows xp partition?

---

