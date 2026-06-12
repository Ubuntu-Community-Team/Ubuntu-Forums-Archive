---
title: "Ubuntu ate my drivers!"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by constructionpaperlawns on 2008-04-03
Hi there,

I've been running Ubuntu 7.10 on my laptop now for a good few months with no problem.  After rebooting  the other night after a few hours of seemingly normal computer use, however, none of my drivers seem to work anymore.  Ubuntu rebooted to an 800x600 resolution screen, no sound, no wireless, none of the things I need to go about my daily routine.  

I dug into the hardware manager and everything seems to be where it should.  All my devices are detected and in the list as they were before, I just don't get any use out of them.  For example, my sound card  seems to be detected, but no device is listed in the sound manager (where you can switch from ALSA to OSS) and an error comes up when I click on the volume app.  My wireless device is also listed in the hardware manager, but doesn't show up at all as a connection I can use in my network manager.  Same seems to go for my nvidia video card, which I went from running at 1280x800 to only being allowed 800x600 or lower.

Without internet, sound, and proper video, I'm pretty much SOL.  Any ideas?  
Thanks

---

### Post by bumanie on 2008-04-03
Was there a kernel upgrade installed on your system? Sometimes new kernels cause conflicts that weren't present before. If you have a previous kernel, try booting with that.

---

