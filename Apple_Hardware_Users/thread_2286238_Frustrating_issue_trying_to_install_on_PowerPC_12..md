---
title: "Frustrating issue trying to install on PowerPC 12.04"
date: 2015-07-10
forum: Apple Hardware Users
---

### Post by tim127 on 2015-07-10
So I've got a powerPC G4 (dead stock except for upgraded ram, see specs here [https://support.apple.com/kb/SP63?locale=en_US](https://support.apple.com/kb/SP63?locale=en_US)) and I can't get the damn thing to boot from CD.  I get to the initial yaboot prompt.  I tried a few exceptions at the yaboot prompt to disable splash screens, nothing worked.  I get the standard white text on black loading, then it goes to a white screen with black text, then goes blank.  No signal whatsoever.  Anyone have any ideas at all?  I'm completely stumped.  Is there an issue with the Nvidia cards?

I also already reset the PRAM and tried multiple ports.  I also had the same issue with a Debian install I tried, of course I got all the way through the text based install but as soon as it would come to the splash screen it would go blank.  If anyone has any tips on that, I'd give it a try.  Debian is currently installed on the hard drive, but like I said, the screen goes blank almost immediately.

---

### Post by rican-linux on 2015-07-10
enter these at boot if you have a radeon card.

```
Linux radeon.modeset=1 video=offb:off video=radeonfb:off radeon.agpmode=-1
```

---

### Post by tim127 on 2015-07-11
It's got an NVIDIA GeForce MX.  I'm going to try a mini iso (which apparently I wasn't doing before, although I thought I was) and see where that gets me.  Apparently a lot of folks had an issue with the Nouveau driver, so I'm thinking this may be the issue.

---

### Post by rican-linux on 2015-07-11
Ok I have more experience with radeon cards than with nvidia on my machines.

---

### Post by CitadelUniversal on 2015-07-11
Have you tried the following help thread? - [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by tim127 on 2015-07-11
I haven't yet.  I'm going to bookmark that.  I'm going to try this guy [http://ubuntuforums.org/showthread.php?t=2131644](http://ubuntuforums.org/showthread.php?t=2131644) first.  Apparently I've exhausted all my re-writes on my CD-RWs so I need to try and find a place that still sells CD-RWs today.

---

### Post by CitadelUniversal on 2015-07-11
What DVD's are you using? It shouldn't have any limit on re-writes for a PC and iMAC. I'm puzzled on this one....

---

### Post by tim127 on 2015-07-11
Not DVDs, CDs.  I never have had problems with DVDs, but CDs seem to have a 10 or so erase limit.  It may also be that I'm now on El Capitan beta, not sure.

Memorex CD-RW, btw.

---

### Post by tim127 on 2015-07-11
Well now I can't even boot from CD anymore.  Just used the Linux nomodeset single command, however, and got into Debian's recovery mode.  Not sure where to go from here.  no wget command

---

### Post by tim127 on 2015-07-11
And I've apparently found out that El Capitan has lost the ability to create iso disks

---

### Post by tim127 on 2015-07-11
Well, gents, I got Ubuntu installed and finally have a gui.  Unfortunately it's obvious the device drivers are incorrect.  All the colors are warped.  Interesting.

---

### Post by este.el.paz on 2015-07-14
> **tim127 said:**
> And I've apparently found out that El Capitan has lost the ability to create iso disks

You can try to change the .iso to .dmg . . . and see if that lets DU burn it.  Giving quick read thru this thread, seems like possibly the optical drive is "failing"??  My 09 MBPro optical drive won't burn DVDs anymore, but will boot them.  Have you tried to boot a USB drive of the iso/dmg file?  Some PPC units will do that and others won't, my iBook doesn't seem to but my old PowMac G4 will . . . ???

e..

edit:  On thewarped colors, try to find the "testers wanted for 12.04" and/or any old threads on "imac800" and read through the advice there.  I think these days the "fbdev" driver might be the choice, then you also have to set the display refresh rates and possibly "horz/vert" in the xorg.conf file . . . or try to run the "xorg -configure" command and see if that sets it up right--have to read the FAQ to tell you how to do that in tha TTY.

---

