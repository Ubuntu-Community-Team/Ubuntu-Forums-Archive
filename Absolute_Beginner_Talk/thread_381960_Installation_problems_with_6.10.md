---
title: "Installation problems with 6.10"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by fopdoodledavid on 2007-03-11
Hi! I'm having touble installing Ubuntu on my laptop. I've downloaded 6.10 and burned it to a CD without any trouble. However, when I put boot up my computer with the CD loaded, I get a "non-system disk or disk error" error message. I don't know a whole lot about the computer, because I got it as a hand-me-down from my dad. Any help on this would be great.

---

### Post by igknighted on 2007-03-11
Do you have a floppy disk in the floppy drive?  You might need to remove that.  Also, are you booting from a pcmcia CD drive?  You need the alternate CD to do that, you can't boot a live CD via pcmcia.  Also, make sure you burned the iso as an image, and not just burning the file onto a CD

---

### Post by wpshooter on 2007-03-11
Fopdood:

Are you sure that the CD drive is set as the FIRST boot device in the BIOS ?

Is there by chance a floppy disk in the floppy drive ?  If so, remove it (while the computer is OFF) and then try booting again.

Good luck.

---

### Post by fopdoodledavid on 2007-03-11
Hey! Thanks for the reply. There's no floppy drive on the laptop, I'm not using a PCMIA card, and I used Infra Recorder to burn the cd, so I don't think burning the cd wrong is the problem. To WPShooter, I'm not exactly sure what BIOS is, so probably not.

---

### Post by houstonbofh on 2007-03-11
Pop the CD in a running windows machine.  If it automounts with neat Ubuntu stuff, it is OK.  If it is a data CD with one file, you burned it incorrectly.  A good step by step is at [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by fopdoodledavid on 2007-03-11
Hey, I ran the CD on a working machine and it came up with a fun little window with lots of programs and stuff. I checked in BIOS (after I figured out what the heck that was) and it says the boot order is first, notebook multibay, then the hard drive, then the ethernet. The same error message comes up when I boot without the cd in the drive, so it could be a problem with the computer, which means I should probably go to a different forum, huh? Any other suggestions would be greatly appreciated. Thank you.

---

### Post by dstew on 2007-03-11
Explore your CD in windows. If you see only one file, with a .iso extension, then you have burned it wrong. You burned it as a data disk, not as an image disk. This might be your problem.

---

### Post by wpshooter on 2007-03-11
> **fopdoodledavid said:**
> Hey, I ran the CD on a working machine and it came up with a fun little window with lots of programs and stuff. I checked in BIOS (after I figured out what the heck that was) and it says the boot order is first, notebook multibay, then the hard drive, then the ethernet. The same error message comes up when I boot without the cd in the drive, so it could be a problem with the computer, which means I should probably go to a different forum, huh? Any other suggestions would be greatly appreciated. Thank you.

Fopdood:

You need to go back into BIOS and see if it is possible to put CD-ROM drive as the FIRST boot device.  Look at the legends at the bottom of the screen to see how to accomplish this.  And if all else fails and if you have it, get out the motherboard/computer user manual and it will tell you how.

As a practical matter the boot order should be Floppy drive 1st, CD-ROM drive 2nd and hard drive 3rd.   And unless needed for some special purpose, I would not place any devices in any higher available boot sequence parameters.

---

### Post by fopdoodledavid on 2007-03-11
Hey, I got it to work! I changed the settings in BIOS to the default, and it booted up just fine. Thank you for your help guys! You're awesome. I'm looking forward to some Ubuntu bliss. Thanks again.

---

### Post by houstonbofh on 2007-03-12
It is always the little stuff that gets you.  I am also a hot rodder.  One time I rebuilt an entire engine for a bad starter. :)  I tell you, it's the little stuff... :)

---

