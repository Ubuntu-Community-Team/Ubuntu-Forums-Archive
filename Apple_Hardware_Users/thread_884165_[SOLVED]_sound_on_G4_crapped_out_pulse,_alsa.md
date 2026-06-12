---
title: "[SOLVED] sound on G4 crapped out pulse, alsa"
date: 2008-08-08
forum: Apple Hardware Users
---

### Post by ubuntubrian on 2008-08-08
G4 TiBook
Hardy Heron
Powermac sound card

I decided to try to get pulse audio working so I could get sound in Firefox media players like swfdec, etc. I followed this wiki after filing a bug for swfdec: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
Alsa had been working fine in 6.06 and I upgraded to 8.04 and sound continued to work, even some players in Firefox.
After the pulse install sound sort of ran then quit running altogether. I uninstalled pulse as per the wiki but still no sound except for a short 1-2 seconds and some system sounds.
This morning I reinstalled pulse as per the wiki and I now have system sounds, beeps and such, and Mplayer has sound but no
other player does, like vlc, xine or xfmedia. This must be a plugin
issue but I don't know which it could be. In xfmedia I get an error:
audio device unavailable, in xine I get a similar error. In VLC I get
this with a flv file:
```
*** PULSEAUDIO: Unable to create stream.
*** PULSEAUDIO: Unable to create stream.
[00000352] alsa audio output error: unable to commit hardware
configuration (Input/output error)
vlc: pcm_pulse.c:115: pulse_stop: Assertion `pcm->stream' failed.
Aborted
```

If I run the sound preferences to test I get this:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument

no matter which device I choose, Alsa, Pulse, Autodetect.

I downloaded the latest alsa-driver source package and built and installed it but that didn't make any difference. I installed every kernel and kernel module that I could think of including smp versions-no difference.

Any ideas?   Thanks

PS-at least I have Mplayer now!



It seems pulse and alsa are not happy.


audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource.

---

### Post by ubuntubrian on 2008-08-09
I have sound again!
I thought of moving my .asoundrc out of the way as it seemed there was a conflict between pulse and alsa. the wiki on pulse had me create or add to that file with some pcm stuff (I had tried this before without success).
In any case I moved it, logged out and in and now have sound all over the system. All the players and even swfdec plugin is playing youtube vids WITH sound!
Sweet!!


 [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

