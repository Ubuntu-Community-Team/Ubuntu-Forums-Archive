---
title: "Help with new audio card"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by outhouse on 2007-06-12
Hello all,
Another dumb question from this old newbie. My onboard audio went out on me, and the only audio card my local store had was a Creative Sound Blaster  X-Fi Xtreme Audio so I got it.  However when I booted up still no sound. I'm dual booting w/ XP even though I don't use it much anymore and the new card works in XP. Can someone push me in the right direction to get it working, or is it even possible? So far my searching hasn't found anything.

---

### Post by Clay_Banger on 2007-06-12
have you disabled the onboard sound in the bios? its generally under "integrated peripherals" > "PCI Devices". 

I think what is happening is that ubuntu is still trying to use the onboard by default and not looking at the new card you put in. if that doesnt work, you will need to tell ubuntu to use the pci sound by default, i cant remember how to do that atm, but if turning the onboard off doesnt work, i'll dig it up for you.

---

### Post by aidanr on 2007-06-12
The X-Fi is not supported, Creative have not provided Linux drivers for it

Creative are apparently working on Linux drivers, but they've been at that for two years, I wouldn't hold my breath

---

### Post by outhouse on 2007-06-22
Gentlemen,
I was able to get my onboard audio working by uninstalling drivers, and downloading new one.(Realtek onboard audio) I have uninstalled Creative PCI card and audio is working fine in XP, but nothing happens in Ubuntu. I've uninstalled and reinstalled Rhythmbox, tried VideoLAN player twice and still can't hear anything. I'm sure it's something simple but I sure am getting mad at myself for not being able to see it. Any help would be greatly appreciated.

---

### Post by r4ik on 2007-06-22
Try,

[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

Good luck !

---

