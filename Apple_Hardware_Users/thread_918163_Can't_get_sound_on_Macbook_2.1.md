---
title: "Can't get sound on Macbook 2.1"
date: 2008-09-12
forum: Apple Hardware Users
---

### Post by liquidfunk on 2008-09-12
I just installed Ubuntu 8.04 onto my 2.1 Generation Macbook. The only thing that refuses to work is the sound. 

 I get sound when I test it in the Sound preferences. I get the beep, however I don't get any other sound at all.

 Ideas anyone?

---

### Post by cyberdork33 on 2008-09-12
check into pulseaudio. It has given a few people trouble.

---

### Post by liquidfunk on 2008-09-13
What do you mean by check into it? Is there anything about the current ALSA release that may be stopping the sound from working?

 The sound worked when I just installed Hardy, then all the updates came, and killed it.

---

### Post by cyberdork33 on 2008-09-13
> **liquidfunk said:**
> What do you mean by check into it? Is there anything about the current ALSA release that may be stopping the sound from working?

 The sound worked when I just installed Hardy, then all the updates came, and killed it.there have been a lot of issues with pulseaudio. It should like the ALSA drivers themselves are working fine if the sound test is working. You can see if there is a fix for it or disable it altogether.

There is this bug too that might be related:
[https://bugs.edge.launchpad.net/mactel-support/+bug/162347](https://bugs.edge.launchpad.net/mactel-support/+bug/162347)

---

### Post by liquidfunk on 2008-09-13
Nope, I can control the sound, but there isn't any. 

 I've tried with Alsa 1.0.0.15/16/ and 17. With no success.

 I have tried the Macbook Ubuntu site. Still nothing.

---

### Post by liquidfunk on 2008-09-13
Nevermind, I solved the problem by booting into the earlier kernel, the 2.6.26.16 then booting back into the .19 kernel. That made the sound work! 

 Although now I get a red light from my Headphone jack.

---

### Post by cyberdork33 on 2008-09-15
> **liquidfunk said:**
> Nevermind, I solved the problem by booting into the earlier kernel, the 2.6.26.16 then booting back into the .19 kernel. That made the sound work! 

 Although now I get a red light from my Headphone jack.

That goes off if you change the switch for digital out.

---

