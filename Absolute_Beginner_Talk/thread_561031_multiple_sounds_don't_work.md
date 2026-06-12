---
title: "multiple sounds don't work"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by LFO on 2007-09-27
Hi  !

distro : ubuntu 7.04
sound-card : SB Live!24 - 7.1

I'm using ALSA and made this file /home/.asoundrc
[quote=.asoundrc]
pcm.!default {
    type plug
    slave.pcm "surround51" // i'm using a 5.1 sound system
    slave.channels 6             // ^
    route_policy duplicate
}[/quote]

I can't get 2 sounds playing in the same time from different apps.
Only the first one that is open can playback sounds.

I understand that my soundcard can't do hardware mixing, i tried to do what this guide : [http://www.sabi.co.uk/Notes/linuxSoundALSA.html#share](http://www.sabi.co.uk/Notes/linuxSoundALSA.html#share) says, but with no result.

Can anyone help  me ?

Thanks.

---

### Post by LFO on 2007-09-27
If i don't use the .asoundrc file i get sounds from different apps but no 5.1 upmix.

Is there any other way to do the upmix ?

ps : sry for the double-post

---

