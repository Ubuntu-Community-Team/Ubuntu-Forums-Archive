---
title: "Help Please! Problem with Install"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by Soles on 2006-02-09
Hi Guys :mrgreen: 

It's my first post here, so don't be too hard on me!! ;) 


When I try to install Ubuntu Breezy, I get this error message..  (isolinux: Disk error 80, AX = 42BA, drive 9F) after only two lines of install codes.  The initial 'Umbuntu' screen looks just as it should, it is after I have pressed 'enter' to start the install, that this error occurs. :( 

I thought that maybe I was burning the image incorrectly, but have now burnt about six discs and always get the same result.  :???: 

The original image file came on the DVD disk from 'Personal Computer World' magazine. I have now downloaded the file (just in-case the first one was corrupt) and burnt a new disk, but got the same results! :confused: 

I then presumed that it is the drive that is at fault and so, have to tried to install Ubuntu on my wife's computer - hey presto, it installs!  The trouble is, I don't want to run it on my wife's PC! :cry: 

I have a Philips DVDR 1628P1 dual layer burner which is nearly brand new and do not have any issues with it normally. 

I decided to check if there were any firmware releases and have just upgraded the drive!

Again, when I come to install i get exactly the same error message! :cry: 

Any help would be much appreciated.

---

### Post by el3ktro on 2006-02-09
You could try and connect your wife's CD drive to your computer and try again.

Tom

---

### Post by wrtrdood on 2006-02-09
From what I can determine, this seems to indicate a BIOS or drive problem.  Since you've tested the CD on a different computer it's not the problem.  You may need a BIOS update.  Also, check that PnP is off.  This can cause some strange problems from time to time.  It may also be DMA related.

---

### Post by bluevoodoo1 on 2006-02-09
[QUOTE=wrtrdood]It may also be DMA related.[/QUOTE]

I had a DMA problem with my install. You can try installing with 'expert.' When you get to the screen about the DVD drive (I forget the exact wording), but there will be a line where you can enter a command. Enter:

```

-d1

```

...and see if it works. That will turn DMA on. It worked for me. Then the rest of the install went perfectly.

EDIT: Your problem is probably hardware related. I have an ASUS DVD-R/CD-R drive and I still have problems with DMA and autoplay staying enabled. That fix above let me install Ubuntu without a hitch.

EDIT2: [http://ubuntuforums.org/showthread.php?t=81600](http://ubuntuforums.org/showthread.php?t=81600)    Look at post 7.

---

### Post by Bartender on 2006-02-09
Never mind

---

### Post by Soles on 2006-02-09
Thank you for your replies guys :mrgreen: 

My bios does have the latest update and I have now unchecked the PnP in the bios!  

All the dma settings seem to be optimal and I have burnt a new disk at seriously low speed (4x) 

The exact same problem still avails tho, so I have to presume it's the drive at fault in some way!  

Am going to swap drives with my wife's PC over the weekend (she'll never notice - except mine's black and hers is biege, yeuk!) and try again! :D 

Will keep you posted!

---

