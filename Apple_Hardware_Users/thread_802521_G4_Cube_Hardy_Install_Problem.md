---
title: "G4 Cube Hardy Install Problem"
date: 2008-05-21
forum: Apple Hardware Users
---

### Post by nhamze on 2008-05-21
I have read the other posts on this message board about getting Hardy working on a g4 cube and I have tried everything in respect to editing the xorg file and I cannot get it to work.  Does anyone know what is the horizontal sync and vertical refresh numbers for a 17 inch adc monitor.  Maybe I have that wrong.

Thanks

Nick

---

### Post by stream303 on 2008-05-22
Need a little more info:

Which version of X/K/Ubuntu are you installing?

Are you trying the live-cd or the "alternate" image?

Are you trying to preserve your original OS, dual-boot it, and/or if so, do you have restore disks?

What is the model of your 17" adc monitor?  Should be pretty easy to find the specs.

How much ram is in the system (if known)?

Are you using the original keyboard / mouse combo, or have you updated them?

I'll leave it to the cube owners for the rest, but this will really help out.

---

### Post by nhamze on 2008-05-22
Which version of X/K/Ubuntu are you installing? Xubuntu

Are you trying the live-cd or the "alternate" image? Alternate

Are you trying to preserve your original OS, dual-boot it, and/or if so, do you have restore disks? I am not preserving OS X

What is the model of your 17" adc monitor? Should be pretty easy to find the specs. It is the apple one, I found a site that had the specs but I put them in my xorg file and it still didn't work

How much ram is in the system (if known)? 768

Are you using the original keyboard / mouse combo, or have you updated them? Original

I tried the exact file that the guy with the 15 inch adc posted and that didn't work and the only thing different between mine and his was the monitor size so I thought the only thing that could be wrong in the resolution and h and vert settings.

Thank you for any help you can give me

Nick

---

### Post by stream303 on 2008-05-23
> **nhamze said:**
> Which version of X/K/Ubuntu are you installing? Xubuntu

Ok, I'm going to assume Hardy 8.04.  If that is the case, then you might possibly want to use the regular Ubuntu instead, since Xubuntu for Hardy doesn't seem to have made it beyond late-beta.  Not that it shouldn't work, but we can cut down any unforeseen variables with regular Ubuntu - once you get it up and running, you can change back to Xubuntu manually.

> Are you trying the live-cd or the "alternate" image? Alternate

Great, usually what I recommend, however you do have so much ram that the live-cd could also be an option.

> Are you trying to preserve your original OS, dual-boot it, and/or if so, do you have restore disks? I am not preserving OS X

Makes partitioning easy!  When you reach guided partitioning, just "use whole disk" instead of the free-space option.  Looks like you did already.

> What is the model of your 17" adc monitor? Should be pretty easy to find the specs. It is the apple one, I found a site that had the specs but I put them in my xorg file and it still didn't work

Here's where it gets sticky. Do you have the 450mhz model or the 500mhz model?  Check it out here:

[http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html](http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html)

If you have the 450mhz model, it came with the option of two different video card, an ATI Rage 128 Pro, or an Nvidia GeForce2 MX card.

For the 500mhz model, you have the choice of the ATI Rage 128 Pro, or an ATI Radeon.

This might be the reason why the video is giving you a problem - you may have to research here for Radeon or Nvidia solutions.

Since you were able to edit the xorg.conf file, can you run the output of

```
lspci
```

and let us know what it says in regards to your video card?  Also what version of X/Ubuntu?  Also, when you boot, do you get a splash screen at all, or does the screen just stay black?  How are you getting to a virtual terminal to make your edits?

---

