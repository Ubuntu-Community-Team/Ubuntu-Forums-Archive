---
title: "ubuntu 7.10 soundblaster (no sound)"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by hashi856 on 2008-04-04
I just installed ubuntu yesterday. I've never used linux before. My problem is, there is no sound. I have a soundblaster x-fi sound card. I click on the volume button and it gives me this error "No volume control GStreamer plugins and/or devices found." I followed the instructions on the "HOWTO: Get your Soundblaster X-Fi to work with Ubuntu" Thread but no luck. Is there another way to get my sound working?

Here is a link to a snap shot of my sound card info [http://s218.photobucket.com/albums/cc73/hashi856/?action=view&current=soundcard.png](http://s218.photobucket.com/albums/cc73/hashi856/?action=view&current=soundcard.png)


[IMG]http://s218.photobucket.com/albums/cc73/hashi856/?action=view&current=soundcard.png[/IMG][/B][/B]

---

### Post by waspbr on 2008-04-05
first of all try writing this in terminal

```
lspci
```

post the output, this will check whether ubuntu sees you card, which it probably will.

I actually have a SB audigy 2 ZS 5.1 and I managed to get it working with alsa, checking out the alsa wiki should probably help ya.

---

### Post by hashi856 on 2008-04-05
I already tried lspci. And alsa didn't have the the driver. Thnks though

---

