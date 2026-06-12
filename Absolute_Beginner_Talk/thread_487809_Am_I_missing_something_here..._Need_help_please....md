---
title: "Am I missing something here...? Need help please..."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-06-29
I don't understand, I have two old computers - one useless without HD, and the other working just fine with Ubuntu. I was messing around with the useless one, when I realized it had a 933Mhz CPU (Versus 533Mhz on the one that works). So I checked and saw they both were Socket370, and put the 933Mhz CPU on the working one. As soon as plugged in the power (and before I pressed an buttons), the PC started running, no lights on the front, PC screen on standby. Confused, I went ahead and put the out CPU in, and it worked perfectly. Is there something I should know?

Current CPU: Intel Celeron 533Mhz
Replacement CPU: Pentium III SL52Q 933Mhz

Working computer: eTower 533id2, 256MB ram, 64MB i810 card

I would really like for this to work, a little extra performance would be nice. ;)

---

### Post by homergreg on 2007-06-29
I'm talking old experience here, but there may be some pin settings on the motherboard that would need to be set up.  I haven't built a computer in a while, but I remember setting the voltage and motherboard clock depending on the processor I was using.  If one has a bad HD, why not just swap HD's?  Does the faster PC boot to it's BIOS?

---

### Post by hardyn on 2007-06-29
move the hard disk to the 933... its easier that bios / motherboard trouble that may occur with a chip swap.  The older motherboard were not always capable of higher clock speeds; i suspect this is what happened... there are also may DIP switched that may have to configured.
move the chip and the hard disk to the other machine, or move the motherboard and processor to the machine with the hard disk.

---

### Post by overdrank on 2007-06-29
> **shamushand said:**
> I don't understand, I have two old computers - one useless without HD, and the other working just fine with Ubuntu. I was messing around with the useless one, when I realized it had a 933Mhz CPU (Versus 533Mhz on the one that works). So I checked and saw they both were Socket370, and put the 933Mhz CPU on the working one. As soon as plugged in the power (and before I pressed an buttons), the PC started running, no lights on the front, PC screen on standby. Confused, I went ahead and put the out CPU in, and it worked perfectly. Is there something I should know?

Current CPU: Intel Celeron 533Mhz
Replacement CPU: Pentium III SL52Q 933Mhz

Working computer: eTower 533id2, 256MB ram, 64MB i810 card

I would really like for this to work, a little extra performance would be nice. ;)

HI the problem is you are going from a Pentium II to a Pentium III like the other post said you may have to change some jumpers. If the 933 does not boot then chances are that it is bad some how. If it does boot to bios then like the other post it would be easier to swap the hard drive unless windows is on it. I am sure that ubuntu can do it may have to reconfigure xorg but chance of window is slim and none. Good luck!

---

### Post by shamushand on 2007-07-02
Here: is what happens:

I put in the new CPU. As soon as I plug the power plug into the wall, the HD start spinning, eventhough everything else is off. The light in front of the computer is off, and monitor is off,but when I press the button in front, the HD stop spinning. Same happens when I press the button again. After much googling, I only found one article related to this, and it turns out you can't upgrade a Celeron to a Pentium III, because of the voltage... Can anyone suggest something else?

---

### Post by shamushand on 2007-07-02
Also, the 933 doesn't have a case, and the stupid motherboard is for those horizontal desktop PC's. I only have one other motherboard, but it's a slot 7... :(

---

