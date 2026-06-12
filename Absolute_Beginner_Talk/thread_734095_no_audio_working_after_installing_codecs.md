---
title: "no audio working after installing codecs"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by 7raTEYdCql on 2008-03-24
i have a acer aspire 5920 laptop.
i have installed all the audio codecs but there is no sound from the laptop.
however if i connect speakers to the laptop then i can get sound.

My laptop speakers are Dolby speakers so do i have to install something else also.

---

### Post by zvacet on 2008-03-25
**System>preferences>volume control>edit>settings>**choose master and PCM  and be sure that is not mute.I hope this will help you.

---

### Post by 7raTEYdCql on 2008-03-25
that does not seem to work.
The very fact that sound does come on external speakers or headphones means there is something to do with the laptop speakers.

i want to know what.
my laptop speakers are dolby home theater. do they have some seperate codecs.


I need help urgently.

---

### Post by kpkeerthi on 2008-03-25
Codecs enable playback of audio files of various formats. Has nothing to do with speakers.

Type ```
alsamixer
``` in a terminal. Make sure the volume levels of mixer channels are raised enough and are not muted. MM indicates Muted. OO indicates unmuted. Use 'm' key to toggle mute/unmute. Use arrow keys to navigate and 'Esc' to quit alsamixer.

---

### Post by northern lights on 2008-03-25
Should nothing have been muted, or the problem persist, post the output of ```
cat /proc/asound/cards
```

---

### Post by superprash2003 on 2008-03-25
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by 7raTEYdCql on 2008-03-25
i have no volume control option under preferences.

---

### Post by northern lights on 2008-03-25
> **i.mehrzad said:**
> i have no volume control option under preferences.
Navigate to "System>Preferences>Main Menu" and add it...

Also, running > **kpkeerthi said:**
> ```
alsamixer
```
from the terminal would work...

---

### Post by Drobbins on 2008-05-06
> **kpkeerthi said:**
> Codecs enable playback of audio files of various formats. Has nothing to do with speakers.

Type ```
alsamixer
``` in a terminal. Make sure the volume levels of mixer channels are raised enough and are not muted. MM indicates Muted. OO indicates unmuted. Use 'm' key to toggle mute/unmute. Use arrow keys to navigate and 'Esc' to quit alsamixer.

This worked a treat when i had the problem, you need to make sure surround and center is not muted 'mm' 

Thanks kpkeerthi
:guitar:

---

