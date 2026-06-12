---
title: "Audio Mixing?? Sometimes!!"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by loudking on 2006-10-18
Hello, all. I have a problem with audio mixing.

It works fine when I play mp3 with Rhythmbox while watching some videos with mplayer. I mean, audio files do mix in this situation.

But when I watch video with realplayer while running Rhythmbox, there is no sound from realplayer, but only the pictures!!

Things are same when I start vmware, it just complains "[COLOR="Red"]Failed to open sound device /dev/dsp: Device or resource busy Virtual device sound will start disconnected.[/COLOR]"

I am using INTEL 82801DB-1CH4(ALSA Mixer). Does anybody know what I should do, please?

Thanks!!

---

### Post by skymt on 2006-10-18
Realplayer and VMWare use OSS rather than ALSA. You can solve this by prefixing the command with "aoss". For example, use "aoss realplayer" instead of just "realplayer". The aoss command comes in the alsa-oss package, so you'll need to install that if you haven't.

---

### Post by loudking on 2006-10-19
no it does not work either!!!](*,) ](*,) ](*,) 

> **skymt said:**
> Realplayer and VMWare use OSS rather than ALSA. You can solve this by prefixing the command with "aoss". For example, use "aoss realplayer" instead of just "realplayer". The aoss command comes in the alsa-oss package, so you'll need to install that if you haven't.

---

### Post by puccaso on 2007-01-14
tried to run aoss vmplayer
but still doesnt work

---

