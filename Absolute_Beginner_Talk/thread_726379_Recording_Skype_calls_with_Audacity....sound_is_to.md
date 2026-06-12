---
title: "Recording Skype calls with Audacity....sound is too fast/compressed"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by HautingLu on 2008-03-16
I gave up trying to record with skype-rec because there was no output files no matter what I tried. I gave this a shot ([http://porpoisehead.net/hi/?q=node/23](http://porpoisehead.net/hi/?q=node/23)) with some success.

Audacity will record fine **up until the moment I place a call**. Then the sound recorded is not normal; sounds like quickened but not quiet "chipmunk" sound. The waveform seems very compressed and doesn't sound right.

I tried everything changing rates to alsa or oss, then going to Sounds options. Nothing.

Anyone experience this also?


On a side note, I tried with Sound Recorder first, but it would **lock up** the second I placed a call (was using alsa). 

I'm going nuts trying to figure this out.

Thanks.

---

### Post by aktiwers on 2008-03-16
Have you tried with "Sound Recorder" in Applications => Sound and video => Sound recorder

I think it will work perfectly :)

---

### Post by anewguy on 2008-03-16
Anyone know if part of the underpinnings is Mlt?   Kdenlive has a problem with sound and according to the posts I have seen it is a bug in Mlt that almost doubles the speed for some people, makes others fast but not double-fast.

---

### Post by HautingLu on 2008-03-16
> **aktiwers said:**
> Have you tried with "Sound Recorder" in Applications => Sound and video => Sound recorder

I think it will work perfectly :)

Thanks for tip, but I tried SR first and it locks up the second I start a call with Skype but otherwise SR works ok.

Audacity was my last hope in getting Skype recordings to work. :(

---

### Post by Redache on 2008-03-16
Are you sure it's not recording at a higher sample rate than Skype uses? if Skype uses say 22000Kbs and Audacity uses 48000Kbs then it might cause the sound you mention.

Try setting audacity to a lower sample rate and see if that helps.

---

### Post by HautingLu on 2008-03-16
> **Redache said:**
> Are you sure it's not recording at a higher sample rate than Skype uses? if Skype uses say 22000Kbs and Audacity uses 48000Kbs then it might cause the sound you mention.

Try setting audacity to a lower sample rate and see if that helps.

I did try to set it a bit lower, with no luck. Maybe my settings are wrong, but I didn't find any write-ups on what those settings should be.

---

