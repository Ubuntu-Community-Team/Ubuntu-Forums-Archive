---
title: "Booting/Installing from the LiveCD"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Cippy on 2007-02-02
Hey guys,
I'm a bit of a n00b with Linux and I'm having some issues just getting the LiveCD to boot properly. I recently burned a copy of the Ubuntu 6.10 image on a CD and tried booting it on my ThinkPad 600E (400 MHz, 228 MB RAM, currently running Windows 2000). I get to the menu, and choose the first option to Install/Boot. The loading screen appears, goes up to 100%, and then a black screen comes on. From here, the following text appears:
> 
[190.255565] Invalid compressed format (err=2)
[190.261940] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)
[190.262016]


I can't type anything or do anything. Eventually, I have to just shut off the ThinkPad through with the power button. Anyone know what I can do? I already burned two CDs of images of Ubuntu 6.10, both times getting the same problem.

Any help is greatly appreciated.

---

### Post by K.Mandla on 2007-02-02
Kernel panics are bad. This probably isn't the suggestion you want to hear, but the live CD is a little finicky at times, and you might have better luck installing from the alternate CD. Have you tried that yet?

---

### Post by Cippy on 2007-02-03
> **K.Mandla said:**
> Kernel panics are bad. This probably isn't the suggestion you want to hear, but the live CD is a little finicky at times, and you might have better luck installing from the alternate CD. Have you tried that yet?

No, but I'm downloading the alternate CD now. Does this one allow me to test out Ubuntu before installation? I'd like to be able to make sure my wireless card works before I install it.

Also, I've been researching this problem more in depth, and one source says lowering the burn speed while burning the LiveCD fixes this issue. My first two CDs were burned at 32x. I'd like confirmation on this before I burn a third CD, because I hate wasting CD-Rs and I'm running low on them.

---

### Post by Maestro23 on 2007-02-03
> **Cippy said:**
> No, but I'm downloading the alternate CD now. Does this one allow me to test out Ubuntu before installation? I'd like to be able to make sure my wireless card works before I install it.

Also, I've been researching this problem more in depth, and one source says lowering the burn speed while burning the LiveCD fixes this issue. My first two CDs were burned at 32x. I'd like confirmation on this before I burn a third CD, because I hate wasting CD-Rs and I'm running low on them.

Burn the disc at the lowest speed possible.  32X is way to fast.

---

### Post by ubername on 2007-02-03
I am also having problems with installing from the 6.10 live CD (search for ubername in the absolute beginners topic) I am currently burning the 6.06 version at x1 speed, to see how I get on. You are not alone!

---

### Post by Cippy on 2007-02-03
> **Maestro23 said:**
> Burn the disc at the lowest speed possible.  32X is way to fast.

Right, but I just got some more information on my CD. I tried out the CD (burned at 32x) on a ThinkPad T30 and everything checked out. Ubuntu booted without any kernel panics. Think changing the speed with affect the performance on my 600E? Or should I just go for the alternate CD? (I'd prefer using the LiveCD to test my wireless card.)

---

### Post by shareMenaPeace on 2007-02-03
For low performance systems you might be better served with XUBUNTU, but i dont know how much the alternate CD in this regard is capable.
[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by jogu on 2007-02-03
Have you tried to boot with the noapic nolapic option?

For example, in the live CD menu:
press F6
add 'noapic nolapic' between 'slash' and '--'

See 'help' in the live CD menu:
F1 and then F6

See also
[https://wiki.ubuntu.com/LaptopTestingTeam/Thinkpad600X](https://wiki.ubuntu.com/LaptopTestingTeam/Thinkpad600X)

---

### Post by Cippy on 2007-02-03
> **jogu said:**
> Have you tried to boot with the noapic nolapic option?

For example, in the live CD menu:
press F6
add 'noapic nolapic' between 'slash' and '--'

See 'help' in the live CD menu:
F1 and then F6

See also
[https://wiki.ubuntu.com/LaptopTestingTeam/Thinkpad600X](https://wiki.ubuntu.com/LaptopTestingTeam/Thinkpad600X)

I just tried them, and no luck.

Should I try burning the Alternate CD?

---

### Post by jogu on 2007-02-03
> **Cippy said:**
> I just tried them, and no luck.

Should I try burning the Alternate CD?

I'm afraid I can't give you advice on that. I'm a beginner too and haven't worked with the alternate CD. I got my HP dv9074 laptop running with these options.

---

### Post by Cippy on 2007-02-04
Alright, the Alternate CD seems to be working, so I'm gonna go with it. Thanks for all the help guys. I'll be sure to return next time I have a problem (gimme a few hours or so ;) ).

---

