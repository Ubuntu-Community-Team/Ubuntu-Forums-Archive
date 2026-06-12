---
title: "iMac G4 won't boot"
date: 2008-09-20
forum: Apple Hardware Users
---

### Post by lixy on 2008-09-20
I have this G4 that decided one morning not to boot. Absolutely nothing happens. I decided to poke it around and went checking the power. Turns out when I plugged the juice in, a hardly audible tick-tick noise would emanate from the unit. After losing all hope, I decided to take it apart to diagnose the problem. That's where I realized that the noise was from the hard-drive.

I don't have a clue how PPC boards work. First thing I did when I got the iMac was install Ubuntu, and it's been a smooth sailing experience. So here's my question: if the hard-drive is defective, shouldn't I be able to get access to some firmware thingy? I don't have any drive compatible with it to test it and it would bum me to buy a new just to discover that the entire board is cooked.

Any help would be appreciated.

---

### Post by liquidfunk on 2008-09-20
I'm no expert, BUT, generally Hard Drive clicking is caused due to lack of power. Is it possible that something on the motherboard isn't functioning properly. In turn not allowing full use of the power unit?

---

### Post by pxwpxw on 2008-09-20
**lixy**

iMac G4 (Flat Panel)
[http://www.apple.com/au/support/imac/g4/](http://www.apple.com/au/support/imac/g4/)

If this is your imacg4, it may provide the answer, in particular if the keyboard and mouse are dead.
  
See resetting PMU, resetting PRAM, accessing OpenFirmware.

---

### Post by lixy on 2008-09-27
Thanks for the replies.

I did some more digging around the unit with a multimeter, and it turned out the noise was actually from the power supply unit. Didn't notice it at first because it's neatly hidden. It's not outputting any voltage, though no component seems burned or anything of the sort.

Now, the half-spherical beast's PSU has two parts: One on the right that takes the 220V and turns it into 12.5V which is fed into the left part that then distributes it to the different components. The noise is clearly emanating from the right unit supposed to lower the voltage from 220V to 12.5V. 

I did some reading on how PSUs work, and it seems a stock transformer is out of the question for reasons of stability. So, I'm actually thinking about getting an ATX unit and hooking up the 12V output to the "left part" of the PSU, and keep the ATX outside of the iMac's case. I'm not convinced it'll work (for one thing, I don't even know if the board is intact) but I might give it a try.

Again, thanks for the interest.

---

