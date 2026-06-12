---
title: "Ubuntu 7.04 Installation Errors"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by YorkerBH on 2007-07-13
I'm a Linux newbie :-P and had just burned Ubuntu 7.04 into my own CD from the website's download. Anyways, when I reboot for starting the CD, it comes up with dozens of errors after I pass the Ubuntu logo in "Start or Install." I tried the APIC Configuration by pressing F6 and typing in "Live noapic nolapic" and it checks the integrity and for errors but does not start "Live CD" option. 

Here are the main errors that show up: :-(

229.931668 SQUASHFS error: sb_bread failed readingblock 0x2e39
229.931726 SQUASHFS error" Unable to read page, block 898ea, size 4c9a

After the error clears, it shows up stuff like "Networking," "Hardware," etc. Then it blanks out with a black screen and my LCD monitor says the "Setting is out of range 1024 X 768 @ 60Hz." 

I heard that some ATI graphic cards can cause problems during install. I have a ATI Radeon 256MB PCI video card 8).

Any help would be greatly appreciated!:biggrin:

---

### Post by shearn89 on 2007-07-13
Have you tried checking the cd's integrity - its something like "check cd for errors" in the first menu that comes up?

---

### Post by YorkerBH on 2007-07-13
Hi shearn89,

     Yes, I checked CD's integrity and it comes out with no errors. Right now I am using my Ubuntu CD through my laptop, so far it's a little slow. I don't get why my HP Pavilion Desktop can't access Ubuntu!

I think it might be the ATI graphics card. Is there anyway I can fix this? I'm not really fond of my laptop as it is slower than my desktop pc, that is why I would like Ubuntu on the desktop.

---

### Post by Cappy on 2007-07-13
Try ```
live noapic nolapic nosplash
```

I think the error indicates that it was misburned though. I would try burning another since it seems to be corrupt somewhere. You might want to check the MD5 on the ISO too. I've burned disks that passed that CD Integrity Check but had similar problems.

---

### Post by YorkerBH on 2007-07-13
Thanks I'll try again right now...but how come it works fine in my laptop? I think it's my graphics card stil.

---

### Post by YorkerBH on 2007-07-13
Ok, I finally got it working though I still can't load Ubuntu because of my ATI graphics card. After it's done with all the "kernel" stuff, it shows up a error about the screen/graphics. I can't quite recall the error message but I knew there was an "X" replying about graphics or mod. Anyways, Linux can detect the screen, but I don't think it can my graphics card.

Anybody, have experience with ATI graphics card error?

---

### Post by shearn89 on 2007-07-14
does it ever say anything about restricted drivers?

---

### Post by YorkerBH on 2007-07-14
Yes, it does say restricted drivers.

---

### Post by macogw on 2007-07-14
Those errors are for it not reading the CD right.  If the cd's fine, it's probably your cd drive, so use a cleaning kit.

This is what I was told after I had this problem with 4 different (perfect) cds.

---

### Post by YorkerBH on 2007-07-14
> **macogw said:**
> Those errors are for it not reading the CD right.  If the cd's fine, it's probably your cd drive, so use a cleaning kit.

This is what I was told after I had this problem with 4 different (perfect) cds.

That's what I was afraid of, but glad too. I need a Lightscribe DC/DVD drive anyways and the CD did work fine on my laptop. Do you mean clean the CD drive's lenses ?

---

### Post by masteryurez on 2007-07-14
THIS WORKS!!

[http://ubuntuforums.org/showthread.php?t=500884&highlight=noapic](http://ubuntuforums.org/showthread.php?t=500884&highlight=noapic)

---

