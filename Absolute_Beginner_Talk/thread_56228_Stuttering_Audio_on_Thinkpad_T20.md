---
title: "Stuttering Audio on Thinkpad T20"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by datassette on 2005-08-11
My audio stutters whenever I do things like minimising a window, a tooltip pops up, or when the HD is accessed.
In 'Multimedia Systems Selector' I have both input and output on ALSA.
The 'test' button in the above mentioned generates a sine wave, which also stutters so I know it's not just mp3s in Rhythmbox which are stuttering.

I imagine the audio buffer might be too low, but I don't know what config file I have to edit to change this.
I've been searching these forums and googling around for the last 2 hours and have found nothing helpful...

The whole reason I installed Ubuntu is to use an mp3 DJ program called GDAM, so getting the audio working properly is essential.

Any advice would be appreciated!

Thanks.

---

### Post by GavinX on 2005-08-11
I've been having similar problems on my T20 as well and I've done some searching to no avail. I probably need to do some further research and see what becomes of it. As a matter of fact, when I used Xandros there was a sound problem also. What used to happen then is that whenever the sound was above a certain level, I would get a loud feedback. It's just one of those things that I'm struggling with still. If you get furtehr inflrmation, please let me know and if I get any I'll be sure to assist you.

Cheers,
GavinX

---

### Post by datassette on 2005-08-11
OK, well I've just followed these instructions from the ubuntuguide:

[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)


Now I have no sound *at all*.
Wonderful.

This is a disaster since the whole reason I'm using Ubuntu (or indeed any form of linux) is for audio, can anyone help?

Thanks in advance for any clues.

---

### Post by varunus on 2005-08-11
Those instructions gave you no sound at all?  Try re-enabling the GNOME sound server and GNOME sounds.  The instructions that tell you to shut them off are wrong in my opinion.

If not, you can undo the changes, y'know.

Audio stuttering problems...Try seeing if any process climbs to high CPU usage when audio stutters.  Also, does the sound act up with ALSA, ESD, or both in the multimedia systems selector?

---

### Post by ReiKn on 2005-09-24
I'm experiencing the same problem with my T20. To avoid stuttering audio while surfing the internet I run firefox through a program called nice. (see man nice for more information).
[INDENT]nice firefox[/INDENT] 
The same works of course with other programs as well. But what it doesn't fix is that audio stutters right after rhythmbox (or bmp) changes song. So I guess this is an issue of CPU usage but I think that a 700MHZ PIII should be able to play audio without stuttering.

---

