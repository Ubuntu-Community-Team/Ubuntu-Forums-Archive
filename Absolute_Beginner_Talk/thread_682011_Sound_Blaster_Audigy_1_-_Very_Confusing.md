---
title: "Sound Blaster Audigy 1 - Very Confusing"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by jsast21 on 2008-01-29
I installed Ubuntu 7.10 about a week ago and I love it - only problem is that I cannot hear any sound out of my SB Audigy 1 sound card. I have spent the last couple of days going through this forum and trying out everything that was suggested to anyone having a sound card problem, especially when it involves the Audigy. The thing is, none of them seem to apply to me or their problem is solved and I still do not have sound.

I have found my sound card on the alsa website ([http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1)), I have gone to the alsa mixer in terminal and made sure nothing was muted.  I am just not sure what to do next. 

Could someone please take me step-by-step through how to troubleshoot / get my sound card to work? It seems like just none of the other posts or How-Tos apply.

Thanks very much in advance.

jsast21

---

### Post by linuxwizard on 2008-01-29
Have you tried this
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab > you could have 3 or 4 settings there look for the one analog/digital unmark it > try playing something

---

### Post by biohypnotix on 2008-01-29
Quoting an old post of mine.

> I have a first generation Sound Blaster Audigy [SB0090] and by default after installing Ubuntu I have no sound. My fix is to open up the Volume Control, go to Switches tab, and untick Analog/Digital output jack box. I have sound then.

---

### Post by jsast21 on 2008-01-29
The Analog/Digital output jack box was ticked, I removed the check and still nothing. To test it out I tried system -> sounds -> test (for the Audigy 1 [Unknown] (ALSA Mixer)) device and I also threw a CD in and played it with Sound Juicer. It is playing, but there is no sound. Not even a system beep.

---

### Post by jsast21 on 2008-02-13
Any other advice? I am totally baffled by the fact that Ubuntu seems to see and recognize my soundcard but I have absolutely no sound. 

Thanks very much for any ideas that you may have.

Regards.

---

### Post by rich41952 on 2008-02-28
Have the same card and trouble with "Intermittent" sound............sometimes I have sound, and sometimes I don't upon re-boot. Try re-booting after un-ticking the analog output box under the "Switches" tab. Hope it works for you!

---

### Post by superprash2003 on 2008-02-29
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by yorkii on 2008-03-01
Same problems here. I have tried the advice in this thread with no results.
There was sound before I unrestricted the ATI drivers I think, which leads me to think that it is a problem there...

---

### Post by yorkii on 2008-03-01
anybody else have this problem?

I have made sure nothing is muted, trued changing the options in the system>preferences.sound section but still no luck with getting sound out

---

### Post by ameik on 2008-03-01
I had the same problem - SB Audigy 1, no sound after the upgrade to 7.10. I tried many things, alsamixer etc. Nothing, until I found this thread - un-checking the "analog" switch seems to have done it. Thanks linuxwizard!.  I have pretty much every channel in alsamixer turned up at this point, including the analog  - I had tried muting that at one point but I don't think that does much by itself - looks like the output jack switch is more important.

---

### Post by yorkii on 2008-03-01
I have turned up all the vlume faders in the mixer and now have pressed the analog/digital switch and I am now able to hear sound from "Listen" or "Rhythm box", but if i play a video in youtube, nothing. also system sound sare not coming through either.

What on earth could the problem be.

---

### Post by yorkii on 2008-03-01
now, I have discovered that Listen and Rhythm box play audio just fine, but the one that I want to use "Amarok" doesn't have sound.

Wow. this is confusing.

---

