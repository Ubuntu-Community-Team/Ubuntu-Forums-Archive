---
title: "Computer isn't Booting"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-10-09
I just got a new Hard Drive and I decided that I might as well reorganize the wires in my case when I install it.  Bad idea. :(  I'm regretting it now because my computer won't boot.  All the fans work, I get the single short beep when I start up, and then it shows the "Infinity" (I have a DFI Infinity Motherboard) screen and hangs there.  I can't get to the BIOS or boot up Ubuntu.  Any help would be appreciated.  Thanks in advance, 

-sheep

---

### Post by meng on 2006-10-09
Are you sure you reconnected everything? correctly?

---

### Post by fatsheep on 2006-10-09
> **meng said:**
> Are you sure you reconnected everything? correctly?

Yes I did check.  Optical Drive and both HDDs have power and IDE cables hooked up.  The large power cord that plugs in directly to the motherboard is attached.  Video card is working properly...

---

### Post by fatsheep on 2006-10-09
I just unplugged my secondary hard disk and it will boot now.  :confused:  However, I want to run both of my hard disks at the same time.

---

### Post by meng on 2006-10-09
Is it something to do with jumper switches? master/slave?
I don't even know if that's relevant anymore, used to be years ago.

---

### Post by fatsheep on 2006-10-09
> **meng said:**
> Is it something to do with jumper switches? master/slave?
I don't even know if that's relevant anymore, used to be years ago.

Yea that was what I was thinking but I'm hesitant to experiment with those jumper switches - I'd probably do more harm then good.

---

### Post by drummer on 2006-10-09
Could be the jumper switches, since the factory default is master, both of them are probably set to that. There should be a diagram on the disk somewhere that shows which pins to put the jumper on for master, slave, and cable select; there's probable also a fourth set of pins and a single pin on one end which you can use to figure out which way round the pins are in relation to the diagram. It shouldn't be too hard to figure out, and it shouldn't break anything if they're wrong, just hang like it was doing I guess.

---

### Post by fatsheep on 2006-10-09
> **drummer said:**
> Could be the jumper switches, since the factory default is master, both of them are probably set to that. There should be a diagram on the disk somewhere that shows which pins to put the jumper on for master, slave, and cable select; there's probable also a fourth set of pins and a single pin on one end which you can use to figure out which way round the pins are in relation to the diagram. It shouldn't be too hard to figure out, and it shouldn't break anything if they're wrong, just hang like it was doing I guess.

Yep it was the jumper switches and I didn't realise that the master had to be plugged into the last connector of my 3 connector IDE cable.

---

