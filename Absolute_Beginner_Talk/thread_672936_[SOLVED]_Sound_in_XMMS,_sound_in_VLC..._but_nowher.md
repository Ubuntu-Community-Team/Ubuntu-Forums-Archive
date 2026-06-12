---
title: "[SOLVED] Sound in XMMS, sound in VLC... but nowhere else."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by LeDechaine on 2008-01-20
Hi.

I can listen to my mp3s in *XMMS*, i get sound coming from *VLC* when I play CDs, and image + sound when i play videos.
..ok, I also get sound from the *system -> preferences -> sound* thing. But that's all. 3 of the 4 tests works, only the last (sound capture, in "audio conference") doesn't. (Gives me an error.)
All of these 4 are set to "*ADC Capture/Standard PCM Playback*"
**Audigy 2 ZS [2001] (Alsa Mixer)** is the sound card I use (if it can help, this is my second sound card in the list, the first being an on-board VIA sound card (**VIA 82C686A/B rev50 (Alsa mixer)**, which i don't [and obviously don't want to] use). There is also an **Analog Devices AD1881A (OSS Mixer)** in the list.)

I **don't** get sound from the "sounds" tab: closing/opening session. (the 2 last play buttons.. 'seems obviously pointless to try the others.)
I **don't** get sound from the "sound juicer", when trying to play a CD. (With VLC, it plays well.)
I **don't** get sound from firefox. (Youtube, or any flash website: no sound.)
I **don't** get sound from my TV Card, which is a **Leadtek Winfast TV2000 XP Expert**.
***(Thread solved yes, but I still don't get sound from this TV card!)***
I **don't** get sound from the *Enemy Territory* game. When started from the terminal, the game tells me that the "sound mixer is muted" or something like that.

But, in alsamixer (typed in the terminal) everything is to the max. Everything is also to the max in the volume control GUI. Nothing is muted, and it's set to the right card, and everything is set to be shown ("tilted" in the preferences).

Anyone can help me? Thanks in advance. :)

*PS: If you don't understand one or some parts of my message, tell me, sorry for my bad english. ;)*

---

### Post by rosegarden78 on 2008-01-20
Even Americans have some bad Engligh from time to time.  Anyway, I used to have problems like these with older distros like Edgy Eft.  Are you using Ubuntu Gutsy or the latest version?  You should always install Ubuntu first before adding KDM and XFCE.  Just backup your files and clean install.  I think that works better than upgrading over the Internet.

---

### Post by rhc on 2008-01-20
[http://ubuntuforums.org/showthread.php?t=548178&highlight=pulse+audio](http://ubuntuforums.org/showthread.php?t=548178&highlight=pulse+audio)

Maybe it will help you.

---

### Post by LeDechaine on 2008-01-20
> **rosegarden78 said:**
> Even Americans have some bad Engligh from time to time.  Anyway, I used to have problems like these with older distros like Edgy Eft.  Are you using Ubuntu Gutsy or the latest version?  You should always install Ubuntu first before adding KDM and XFCE.  Just backup your files and clean install.  I think that works better than upgrading over the Internet.

Hmm.. the problem is *this* is a clean install.. 'just installed Ubuntu this week! (Ubuntu 7.10)
And I don't even know what KDM is (though i know what XFCE is).. but both aren't installed, i'm using gnome.

> **rhc said:**
> [http://ubuntuforums.org/showthread.php?t=548178&highlight=pulse+audio](http://ubuntuforums.org/showthread.php?t=548178&highlight=pulse+audio)

Maybe it will help you.

Damn, forgot to mention I was using Ubuntu 7.10..
And.. I think the problem is only that the card is misconfigured somewhere, no? =/

---

### Post by rhc on 2008-01-21
I configured that Pulse Audio for 7.10 too.
But i don't know if it ll work for you.
I had a problem before and solved it with Pulse.

---

### Post by MegaJim on 2008-01-21
My first suggestion would be to disable your onboard audio card in the bios, as you're not using it anyway and it being there just causes resources to be wasted.

---

### Post by LeDechaine on 2008-01-21
> **MegaJim said:**
> My first suggestion would be to disable your onboard audio card in the bios, as you're not using it anyway and it being there just causes resources to be wasted.
Yeah that was my first idea too.. I'll do it.. when i'll reboot.. in one or more weeks (haha!)
And if it doesn't do the job i'll mess with PulseAudio :P

---

### Post by LeDechaine on 2008-01-30
Yahoo, just disabled my onboard audio card in the bios and sound works with everything in the list!

I only don't get sound from my Winfast TV2000 XP Expert card, but well, i'll mess with this soon.
Thanks! :D

---

