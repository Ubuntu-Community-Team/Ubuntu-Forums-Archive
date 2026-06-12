---
title: "G4 Mini ALSA sound problem"
date: 2008-06-03
forum: Apple Hardware Users
---

### Post by guddler on 2008-06-03
Not just the normal "it doesn't work" ;)

Actually, it works fine. I'm running 8.04 PPC and in X all sound is great including the volume control. Problem is, the app that I want to run (advance mame) refuses to recognise that ALSA is available when I execute the configure stage of the compile. I should probably clarify that I am actually running from the console - I don't want X as I'm running a resolution of 640x248-16@15.75Khz.

My suspicion is that perhaps something major has changed in ALSA over the last couple of years as advmame has not been maintained since June 2006.

Is anyone able to offer any help as to what I might need to do to get configure to recognise that ALSA is indeed installed, and, as far as I can tell, so are the development libraries.

Oh, the crux of my problem is that when it uses OSS for sound the volume is only controllable between 0 and -40. 0 being "Speakers are going to split" loud, -39 being "sound really distorted loud" and -40 being off. I've spent about 12 hours now investigating this and just feel I may get somewhere if I can get advmame to use ALSA.

Thanks,
Martin.

---

### Post by guddler on 2008-06-03
Since I can't find where to delete this post, a quick update!

Lack of sleep must have been clouding my vision. I found where the include files for the ALSA libs were meant to be and despite all my efforts yesterday, they weren't installed after all. I've now installed them and am compiling ALSA support into the program. I'll know in an hour or so if it's resolved the issue I was having.

---

