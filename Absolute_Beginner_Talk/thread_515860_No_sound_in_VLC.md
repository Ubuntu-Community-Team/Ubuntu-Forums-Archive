---
title: "No sound in VLC"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-08-02
Why is there no sound in VLC? Any special configuration required? Although the movie runs but the sound doesnt work.However it works in Windows (I mean VLC). Any suggestions? Thanks.

---

### Post by p_quarles on 2007-08-02
No special configuration is required. If it's not working, it's some kind of bug.

Have you installed the all the extra codecs? Is it possible that another device is using the soundcard while you're trying to play the video? Does audio work otherwise?

---

### Post by Inxsible on 2007-08-02
Assuming that the sound works in other apps and the problem is only in VLC.

Start up VLC. Go to Settings --> Preferences --> Audio --> Output modules. Enable the advanced options on the bottom right corner. Change the Audio output from ALSA to Linux OSS.

Restart VLC.

That should do it !

The ALSA in the VLC is broken, and we need to use OSS to be able to play sound.

---

### Post by the ev on 2007-12-21
Tried switching to OSS, but still no go.  VLC reopens muted, but turning the volume up in VLC doesn't work.  Sound works fine across all my other apps, and I can play the same movies in Movie Player with sound.

Any suggestions? Running Gusty i386.

---

### Post by drs305 on 2007-12-21
If you play a straight audio file do you get audio? Perhaps we can isolate it to a general audio problem or something specific to video.

---

### Post by the ev on 2007-12-22
At first, no.  Then I realized that I had paused my music in Banshee and that was still paused in the background.  After quitting Banshee, VLC had sound in both movies & music.  Does this mean I can only use one program for multimedia with sound at a time?

---

### Post by easilydistrac on 2008-02-11
I'm having this same problem, tried switching to OSS, with no result.

I have an intel HDA sound card, but I fixed the codecs (i thought)

sound works for everything except VLC, but I'm not lucky enough to have banshee running.

Can anyone help?

---

### Post by joeshack on 2008-02-23
may want to try turning off your system sounds. worked for me.

---

### Post by lingnoi on 2008-02-23
> **the ev said:**
> Does this mean I can only use one program for multimedia with sound at a time?

For any OSS using apps try 

```
aoss vlc
```
replacing vlc with whatever app you want.

aoss converts OSS apps to ALSA apps so it should allow you to have both playing.

---

### Post by konungursvia on 2008-02-24
For some installs sound only works with one device. Try installing the alsa backports.

---

