---
title: "CPU Overheating/Fan Control?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by bladerunner060 on 2007-10-27
I've looked for awhile now and haven't found a thread that directly addresses what's going on with me...or at least, not one that I can get.  i figured I'd post here for help in the "Absolute Beginner Talk" so I could get a nice, dumbed down answer

i'm a brand-spanking new know-nothing user, switching from XP on my laptop.  System's set up for dual boot on a partition, I dled a live CD, installed, then upgrated to 7.10, which fixed my broadcom chipset problem (yay!) nicely, though I'd already found a fix in the interweb.  I have a compaq Presario v5000, and I've been noticing 2 things; the system occasionally goes 'wonky' (windows closing occasionally, for no apparent reason, things moving, the keyboard acting like I'm holding a key down when I'm definitely not, and it only stops when i hit that or any other key, touchpad goes crazy).  I've also noticed teh thing seems to be running hotter than it used to.  I installed lm-sensors, and its pretty much always above 50C; documentation i found online said that's way too hot for this particular comp, by several degs.  I was wondering if there's some way I can control the Fan speed, as I think it's coming on less and that might be at least part of why it's hotter?  Thanks!!

---

### Post by Crafty Kisses on 2007-10-27
> **bladerunner060 said:**
> I've looked for awhile now and haven't found a thread that directly addresses what's going on with me...or at least, not one that I can get.  i figured I'd post here for help in the "Absolute Beginner Talk" so I could get a nice, dumbed down answer

i'm a brand-spanking new know-nothing user, switching from XP on my laptop.  System's set up for dual boot on a partition, I dled a live CD, installed, then upgrated to 7.10, which fixed my broadcom chipset problem (yay!) nicely, though I'd already found a fix in the interweb.  I have a compaq Presario v5000, and I've been noticing 2 things; the system occasionally goes 'wonky' (windows closing occasionally, for no apparent reason, things moving, the keyboard acting like I'm holding a key down when I'm definitely not, and it only stops when i hit that or any other key, touchpad goes crazy).  I've also noticed teh thing seems to be running hotter than it used to.  I installed lm-sensors, and its pretty much always above 50C; documentation i found online said that's way too hot for this particular comp, by several degs.  I was wondering if there's some way I can control the Fan speed, as I think it's coming on less and that might be at least part of why it's hotter?  Thanks!!

You can always check your tempature while you're in Ubuntu.
```
acpi -t
```

---

### Post by bladerunner060 on 2007-10-27
sensors tells me 55C,

acpi -t tells me 0.0C


is there a default fan speed control?  I use AC most of the time, and I don't care about noise much, so i really wouldn't even mind if it was on all the time, tho controllable = better

---

### Post by MolotovHearts on 2007-10-27
My computer used to over heat and turn off, so I just opened the tower and vacuumed around the fan and the vents. Is there a similar thing that could be done for a laptop?

---

### Post by bladerunner060 on 2007-10-31
Yeah, mostly.  I did that, though, blew out all the dust and such.   I'm coming down to thinking that the issue is the fan's only coming on when it ABSOLUTELY NEEDS TO to avoid fragging, and I'd like a little more leeway in the temperature, like to have it come on a few degrees sooner, and I don't know how to do that.

---

