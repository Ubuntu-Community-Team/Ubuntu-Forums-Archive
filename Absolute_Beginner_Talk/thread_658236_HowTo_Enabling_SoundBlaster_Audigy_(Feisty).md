---
title: "HowTo: Enabling SoundBlaster Audigy (Feisty)"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by mustbealennox on 2008-01-04
Posting this for the benefit of other newbies.

I followed the instructions on this thread, and compiled/installed the latest alsa libraries:
[http://ubuntuforums.org/showthread.php?t=628305&highlight=sound](http://ubuntuforums.org/showthread.php?t=628305&highlight=sound)

I also verified that the system knew about my sound card, and that is was the default one:
aplay -l
lspci
(note that if you have multiple devices, there are other threads that deal with how to ensure your device is selected)

From the system menu, I also verified that the sound card was the default one:
System -> Preferences -> Sound
- verify the sound card is selected in the drop down Devices menu of the Default Mixer Tracks

Then I verified that the alsamixer did NOT have the channels muted
alsamixer

Still no sound ...

Then I opened the Volume Control application (speaker icon in the top right), verified all levels were ok, and changed to the "Swiches" window. On a whim, I deselected the Audigy Analog/Digital Output Jack.

It was a beautiful moment. I hope someone finds this useful. It took me 2 months to finally put all the pieces together.

---

### Post by julian67 on 2008-01-09
There should be no need to recompile ALSA for the Audigy card, the Ubuntu installer takes care of everything. Mine was fine, all I had to do was uncheck a switch in the mixer GUI and it worked right away. It worked fine both with Feisty and Gutsy.

---

