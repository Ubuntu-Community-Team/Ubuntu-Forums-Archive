---
title: "Sound broken? Ears almost bleeding.."
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Geek33 on 2007-03-06
I just got Ubuntu to load off the Live CD after struggling with my fussy ATI graphics card, and I opened one of the Example .oggs but there was no sound.

I went to System -> Preferences -> Sound and changed all the things there to USB Device...when I tested them the beep was so loud I thought I was deaf. <_<

Even with my headphones a few feet away on the desk, with the sound muted on the volume control on their cable...the volume muted up near the clock..it still makes a VERY loud beep when I test the sound, or god forbid open a file with sound it makes it horribly loud..

Any fixes? :\ I couldn't find anything on the forums about this...it's a Plantronics headset if that matters..I'm not sure the make, but it recognizes that it's plugged into the USB.

For now I'll leave them unplugged as sound isn't that important to me, but I dont' want my headphones to not be usable ever. :(

---

### Post by taurus on 2007-03-06
Open a terminal and lower the volume with this command (you use the arrows to move and increase or decrease the volumes).

```
alsamixer
```

---

### Post by Geek33 on 2007-03-06
Did this, changed Master from 80 to 0, and Headphone from like 75 to 0...muted everything, and still just an obscene amount of sound. o_o

Anything else I could try? :\ I tried all the other possible selections other than USB Device under Sound Preferences...a few gave the beep and the rest were silent (even with normal volume on).

---

### Post by saracen on 2007-03-08
Similar issues over here.  It seems like the volume control from the headset isn't working properly.  To fix this you'll need to open up the volume control application by double-clicking on the little speaker icon in the upper right (next to the date).  Then go to File -> Change Device and select your headset.  Then under the Playback tab you should have a volume control slider for PCM.  Play with that and it should adjust the volume appropriately.

Have you filed a bug for this in launchpad?

---

