---
title: "Microphone works but Sound Recorder doesn't record anything"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by HautingLu on 2008-03-03
I'm hoping that if I can get Sound Recorder to work, then Skype-rec (Skype call recording program) will also work. 

I've followed a lot of the threads here about switching to oss, but it still won't record. Skype works fine and I can hear the microphone fine. If I goto into Preferences -> Sound, and test the mic input, the level doesn't change at all.

I've also played with all the settings in the Volume Control settings.

Is there something I'm missing?


p.s. using an old archieved thread I was able to get a command line recording to work, but not Sound Recorder.


Thanks.

---

### Post by buckeyered80 on 2008-03-05
I messed with that for a day or two.  The main thing I was missing was the capture setting.  It needs to be set to record and turned up.  Also, you may need to set your card to full duplex.  I set mine to full duplex and 44100 hz sampling rate.  You can do that in the advanced tab under Sounds and multimedia in the System settings.  I use Kubuntu, may be a little different in Ubuntu.  Hope that gives you an idea.

---

