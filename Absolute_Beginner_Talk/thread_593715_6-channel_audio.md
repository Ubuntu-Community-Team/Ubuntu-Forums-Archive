---
title: "6-channel audio?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by kevind23 on 2007-10-27
I am running Ubuntu x86_64.

I have an awesome set of [6-channel speakers](http://www.logitech.com/index.cfm/speakers_audio/home_pc_speakers/devices/224&cl=us,en) (okay, 5.1 surround, but it needs to output as 6 channels) and only an integrated sound card (Realtek AC'97 I believe). They worked fine on windoze, but linux refuses to output anything more than 2 channels of audio. I have tried messing with the Sound Configuration but it doesn't do any good.

Is there some plugin/driver/anything that I need to get? Because I want my surround sound back T_T

---

### Post by sad_iq on 2007-10-27
Try writing in a terminal **alsamixer** and raise the volumes till you get the desired effect :popcorn:

---

### Post by kevind23 on 2007-10-27
> **sad_iq said:**
> Try writing in a terminal **alsamixer** and raise the volumes till you get the desired effect :popcorn:

The volumes were already raised to the max. And still I only get 2-channels. Perhaps it has to do with the fact that I don't have any authentic surround stuff to play because it won't play DVD's ><

---

### Post by sad_iq on 2007-10-28
In alsamixer scroll to find the [COLOR="Red"]Chanel[/COLOR] tab, make sure it is in 6ch placed, also make sure downmix is off, [COLOR="red"]Spread F[/COLOR] is not muted(press m tu mute or unmute), Play with the [COLOR="red"]Surround[/COLOR] tab, see if it makes a diference.

---

