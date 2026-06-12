---
title: "Sound Problem"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-12-07
i am using Gutsy Gibbon on Yamaha724. Actually i have two sound cards, one of Realtek that's builtin to the motherbaord, which doesnt work. While the Yamaha one works good on windows and Linux.

The problem is this that i can hear the sound of 
System > Preferences > Sound 
Beeps, and the messages that i recieve in pidgin also give me the sound, but there is no sound of media player whether i play it on mplayer or vlc, or helix, or whatever, whether its an mp3, ogg, avi o whatever.....
What could be the problem?

---

### Post by shoaibi on 2007-12-07
This might help:
```

mplayer -ao help
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Available audio output drivers:
        oss     OSS/ioctl audio output
        alsa    ALSA-0.9.x-1.x audio output
        arts    aRts audio output
        esd     EsounD audio output
        pulse   PulseAudio audio output
        jack    JACK audio output
        nas     NAS audio output
        sdl     SDLlib audio output
        openal  OpenAL audio output
        mpegpes DVB audio output
        v4l2    V4L2 MPEG Audio Decoder output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output

```

Alsa is the HDA Intel, which doesnt work anymore. While YMPCI isn't shown anywhere..

---

### Post by Riffer on 2007-12-07
Do you have the proper codecs installed?

---

### Post by shoaibi on 2007-12-07
i have the following:
```

w32codecs ubuntu-restricted-extras gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll vlc vlc-plugin-* mozilla-plugin-vlc avahi-daemon avahi-utils amarok k3b libk3b2-mp3 


```

---

### Post by Riffer on 2007-12-07
Sorry thats about all I can think of.  I'm not sure if your using the onboard sound or a sound card.  

Also some sound is usb based which could cause some problems.  I'm not sure if your card falls into that category.

---

### Post by shoaibi on 2007-12-07
Yamaha 724 is a sound card, that i have in my PCI slot, its not embedded on the board, neither it is usb...

---

### Post by shoaibi on 2007-12-09
Here is the most strange thing that i ever experienced.
I am using Windows XP inside VMware.
I ran WMware, Ran Windows XP, And then for some reason i minimized it and ran Counter strike in Wine, and i got the sound. I closed it and started a movie, but there wasn't any sound. Now i just started hit and trial, and i opened a song in Windows XP inside VMware, so that VMware shows that sound card is busy and being used by windows xp. I minimized VMware, played a movie and this time Voilla everything gives me sound.

If i play a some sound inside VMware on Windows XP, that sound is not hearable, but after that when i play something in Ubuntu, it gives sound. Vice Versa is also true.

---

### Post by Dave Otter on 2007-12-09
I use the same card as you.
    Try opening terminal and type asoundconf list
   Then type in asoundconf set-default-cardCARD
   replacing CARD with the card of your choice

---

