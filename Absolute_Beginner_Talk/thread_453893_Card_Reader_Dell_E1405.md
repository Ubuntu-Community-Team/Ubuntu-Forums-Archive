---
title: "Card Reader Dell E1405"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by .adma on 2007-05-24
I can't get my card reader to work that well  :(  If it is in the computer when Ubuntu loads, I can use it perfectly...if I take it out, then put it back in...it ignores it.  Actually, I can go and see that it is there, but if I try to access it it says "you are not priveledged to mount the volume."  

Below is my hardware...thank you so much to whoever can help me make this work!!

```
...
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
...

```

---

### Post by n8bounds on 2007-05-25
boot without a card in, try this from a terminal:

sudo setpci -s 02:01.1 4c.b=02 

and then stick a card in, and tell me what happens

---

### Post by .adma on 2007-05-28
just saw your reply, sorry about that!  I was without internet all weekend...oddly enough, the way I fixed the issue was to comment out the line in the FSTAB file that set up permissions for the MMC card.  Odd huh?

---

### Post by Sam Lars on 2008-06-07
I have the same hardware, except at 2:09.0-4, and it's built in.
I think it works with SD cards, but I can't get it to work with Memory Sticks.  I tried your command and it didn't do anything.

---

