---
title: "Asus UL50VT booting problems (graphics-related)"
date: 2011-07-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Fishkins on 2011-07-20
Thanks for taking a look at my problem. I'm dual-booting Windows 7 and Natty Narwhal on an Asus UL50VT laptop. It was working for a while, although I couldn't run Unity because I hadn't taken steps to enable the nvidia graphics card. Around a week ago, however, I stopped being able to boot Ubuntu at all. I hadn't made any major changes, so I assume it was caused by some update. I end up with some text instructions displayed on the screen, and then nothing more happens (here's what I see, in case that's relevant: [http://i1219.photobucket.com/albums/dd427/Naliba/Errors/IMAG0015.jpg](http://i1219.photobucket.com/albums/dd427/Naliba/Errors/IMAG0015.jpg)  or [http://i1219.photobucket.com/albums/dd427/Naliba/Errors/IMAG0006.jpg](http://i1219.photobucket.com/albums/dd427/Naliba/Errors/IMAG0006.jpg)).

If I boot in recovery mode and choose the minimal graphics option, I can start Ubuntu. I get a message about it not being able to recognize my monitor, but it basically works.

I want to get the nvidia drivers working in hopes that it will fix my boot problem, and maybe allow me to run Unity. I've tried to follow the instructions at [http://www.grimsby.us/?p=70#more-70](http://www.grimsby.us/?p=70#more-70), but I haven't been able to get into the BIOS settings. I think it's because I'm not able to boot far enough to access them, but maybe I'm just missing something.

What should I do next to try to fix this problem?

---

### Post by Fishkins on 2011-07-31
Okay, I guess the problem was just that I had created an xorg.conf file, and that was crashing Ubuntu. I changed to SATA setting in the BIOS to compatibility mode, which made Ubuntu recognize the nvidia driver. The problem now is that it no longer detects my monitors for some reason. I ended up deleting my xorg.conf file and switching SATA back to enhanced. I'd rather have access to my external monitor and have the worse graphics card than have the good graphics on one screen, but if anyone has any suggestions about how I could achieve both, that would be appreciated.

---

