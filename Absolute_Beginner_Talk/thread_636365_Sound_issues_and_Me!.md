---
title: "Sound issues and Me!"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by liv2lrn on 2007-12-09
Wow where do I begin?
 I'm new to this Linux/Ubuntu/Gnome stuff. Between the apt-gets and the sudos and nautilis' I honestly thought I'd lose my mind.
I first installed Ubuntu Gutsy on my laptop, Toshiba A105 4074, I didn't have any real sound. It was like listening to the dare thing muted. I tried installing OSS and reconfiguring the drivers uninstalling and reinstalling alsa drivers. I finally got that fixed by following the instructions here [http://ubuntuforums.org/showthread.php?t=416207&highlight=sound ](http://ubuntuforums.org/showthread.php?t=416207&highlight=sound ) .
I was so pleased with myself that I went ahead and installed the Adobe Flash Player 9. Come to find out it would not play sound with the flash files on you tube... ect. I went on another wild campaign to find a fix for this. I finally found one that coincidently worked with Pulse Audio which I had installed earlier trying to fix my sound issues. You can find this fix here [http://pulseaudio.vdbonline.net/libflashsupport/](http://pulseaudio.vdbonline.net/libflashsupport/) . I  just installed  this using the .deb file, now all my audio is back online.
I can not tell you how much I have learned from this ordeal. I'm truly impressed with the knowledgeable  people on this site. It took a lot of hunting and I hope my story will help some other lost soul.

---

### Post by nikoPSK on 2007-12-09
possibly you don't need alpha drivers? I did not. You can try as follows:

```
asoundconf list
```

That'll list all sound output devices recognized.

```
asoundconf set-default-card XXX
```

In my case it was "Audigy". I also had to play around in alsa mixer a bit.

---

