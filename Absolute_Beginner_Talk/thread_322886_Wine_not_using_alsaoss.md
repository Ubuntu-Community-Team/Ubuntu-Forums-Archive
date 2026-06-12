---
title: "Wine not using alsaoss?"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Pobega on 2006-12-21
Well I've been searching through the forums for ways to make multiple things play sound, and I think I have got it working 90% for programs. But whenever Wine runs a program, it doesn't want to play sound alongside XMMS!

What I'm trying to do is play Dofus (A flash-based MMORPG) through Wine with the SFX on, and XMMS playing in the background. But no matter what I do it doesn't seem to want to play alongside XMMS (Although virtually anything else will). I've went through the steps in almost every thread I found using the search on the forums, but nothing works for me.

Does anyone have any more ideas? Could it be something with flash player's output? (I'm running the flash files through an exe, because Firefox won't let them connect to the internet. Otherwise it would probably work alongside everything.)

---

### Post by beniwtv on 2006-12-21
Normally, you have to configure wine to use ALSA first.

Run winecfg, go to the Audio tab, deselect OSS and select ALSA.

Also, XMMS has to be configured to use ALSA as well.

Have you done this?

Hope this helps.

---

### Post by Pobega on 2006-12-21
> **beniwtv said:**
> Normally, you have to configure wine to use ALSA first.

Run winecfg, go to the Audio tab, deselect OSS and select ALSA.

Also, XMMS has to be configured to use ALSA as well.

Have you done this?

Hope this helps.

Yes thank you, that worked perfectly! I didn't know about winecfg, should be helpful in the future.

Thanks for the quick reply, the support here is so awesome.

---

### Post by beniwtv on 2006-12-21
> **Pobega said:**
> Yes thank you, that worked perfectly! I didn't know about winecfg, should be helpful in the future.

Thanks for the quick reply, the support here is so awesome.

You're welcome. And ask every question you have ;)

---

