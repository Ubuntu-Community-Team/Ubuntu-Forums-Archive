---
title: "vlc-esd"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by skifreak_rm on 2008-02-12
I can't get mp3 files to play in VLC.  I've heard installing vlc-esd would fix it, but I don't know how.

Could someone show me where to download, and explain how to install that?

Thanks.

---

### Post by jaytek13 on 2008-02-12
Had you installed the codecs to play mp3's previously and now they just aren't working specifically with VLC, or you can't play mp3's with anything?

---

### Post by jan quark on 2008-02-12
hmm

vlc should support mp3 from the very beginning 
perhaps you have to install the ubuntu-restricted-extras
package from synaptic to enable the mp3 support in the first place

---

### Post by skifreak_rm on 2008-02-12
I now think the problem is that VLC does not recognize my sound card.  I am using the M-Audio Audiophile 24/96 and it is listed as /dev/audio2.  I think VLC is mistakenly using dev/audio.  In VLC I have tried to change the audio output modules, choosing in turn "Default" then "ALSA audio output" then "Linux OSS audio output" and all other choices.  None of them work.  Is there a way to direct VLC directly to /dev/audio2?  This is how I got GNOME Wave Cleaner to work.  The problem is not just with MP3 files as I cannot hear .WAV files either.  VLC is playing them, they are just not getting to my soundcard.

---

