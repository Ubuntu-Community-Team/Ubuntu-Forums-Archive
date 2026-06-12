---
title: "audio is mute under gusty"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by bkelly on 2008-02-09
I am running Gutsy on and X86 architecture, 64 bit.  There is no sound what so ever.  Using System | Preferences | Sounds all items are Autodetect.  Selecting Test for Sound Playback produces nothing at all.  The little testing bargraph runs back and forth, but I hear nothing.  The speaker icon at the top appears to NOT be muted.  I have tried this with speakers plugged in and not plugged in.  

Where do I start checking?

---

### Post by PaulFr on 2008-02-09
**[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)**

---

### Post by bkelly on 2008-02-09
I followed the link from PaulFR and the system responded as follows:


bkelly@DESQ:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bkelly@DESQ:~$ 

I interpret this as saying that a sound device has been detected, but I cannot tell anything about it.  The speak in the tool bar does not show muted.

---

### Post by PaulFr on 2008-02-09
So, as per the link I posted, please proceed to the **Using alsamixer** section which is further down the page.

Also, there is a long running thread in Ubuntu Forums (**[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)**) about sound problems in Ubuntu. Please review that for a sequence of steps.

You can search for your specific sound card for other related threads in Ubuntu Forums.

Best of luck !

---

### Post by Bubba64 on 2008-02-10
On my computer when I open sound from system preferences I have oss as the sound playback and alsa in sound conferencing and the actual sound card in device. You can open your volume control and click on edit and make sure your card is the one marked I also installed Gnome Alsa mixer on my computer so that I could access all parts and make sure nothing is muted. You can also click on edit preferences in the volume control and add all of the options to make sure nothing is muted.

---

