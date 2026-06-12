---
title: "Looking for assistance with new graphics card, not being  recognized, ATI Rad1650 Pro"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by freshsyndicate on 2007-08-23
hi
I have installed a new graphics card on my pc. My pc is a gateway GT5432 with a new total of 3Gbs of RAM, everything else is stock....dual core processor...320Gb harddrive...etc... 
Anyways the new graphics card is installed, but isnt recognized and cannot figure out whats issing wrong...
The "stock"  graphics card is an onboard Nvidia 128mb, and have already disabled it, yet new card isnt recognized. Also the cd didnt install, and still the card is disabled.
The new card is an ATI Radeon X1650 Pro AGP 512mb DDR2. I chose this card because it was on sale, vista ready..which i have, and AGP is faster so i chose this over PCI or PCI express. Could this perhaps be the problem, should i have chosen PCI???
I purchased an extra 4 pin power cord since my previous power cord was not long enough, therefore now the new card is entirely installed (power inserted into the AGP slot) yet the computer still dosnt recognize it.
If anyone can help me at all, it would be great, please and thanks.

---

### Post by dougfractal on 2007-08-23
> yet the computer still dosnt recognize it.

Do you mean at bootup you see nothing, or the liveCD froze at some point, is so wath was the last thing you saw?

---

### Post by alienexplorers on 2007-08-23
When you turn your computer on do you mean you do not see the initial startup screen?

---

### Post by klytu on 2007-08-23
> **freshsyndicate said:**
> hi
I have installed a new graphics card on my pc. My pc is a gateway GT5432 with a new total of 3Gbs of RAM, everything else is stock....dual core processor...320Gb harddrive...etc... 
Anyways the new graphics card is installed, but isnt recognized and cannot figure out whats issing wrong...
The "stock"  graphics card is an onboard Nvidia 128mb, and have already disabled it, yet new card isnt recognized. Also the cd didnt install, and still the card is disabled.
The new card is an ATI Radeon X1650 Pro AGP 512mb DDR2. I chose this card because it was on sale, vista ready..which i have, and AGP is faster so i chose this over PCI or PCI express. Could this perhaps be the problem, should i have chosen PCI???
I purchased an extra 4 pin power cord since my previous power cord was not long enough, therefore now the new card is entirely installed (power inserted into the AGP slot) yet the computer still dosnt recognize it.
If anyone can help me at all, it would be great, please and thanks.

I have the PCI-e version of this card installed and it works great in Fiesty. Does the card work when you are running Vista? I know  I had to download updated drivers from ATI for the card to work properly in Vista; the drivers on the CD that came with the card were useless under Vista. 

And, as others have asked, what do you mean when you say it isn't recognized? Do you mean that when you are running Ubuntu now, with the new card installed, you have no display at all?

---

### Post by Tyke91 on 2007-08-23
can you start ubuntu in safe mode, run this code 

```
lshw -businfo
```

post the info that goes with your graphics card... then

```
cat /etc/X11/xorg.conf
```

and post the group of lines that has to do with your graphics card (you should see it's name on the side)

---

