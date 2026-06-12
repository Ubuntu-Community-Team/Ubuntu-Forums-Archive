---
title: "It Seems I just Lost my Audio Driver"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Pirschjaeger on 2007-08-07
Hi All,

well, it's just as the title says. 

Since I first started using Ubuntu with the goal of total conversion, I've had 3 main problems (keyboard, resolution, and skype/mic). The first and second have been solved but the last, the mic, has bit a bit of a bugger.

Finally, after searching this forum and finding little tidbits here and there, I got the mic working under Skype, but only for about ten mins. What I'd done is set everything to oss instead of Alsa; even in Skype. Although the person I was speaking to halfway round the globe said it sounded like I was on Mars, I was happy to at least make sound. During our discussion I tried playing with the settings to see if I could make my voice clearer. In options I changed "shared line in" from "mic in" to "line in". My pc immediately froze and I had to do a forced reboot. Once my rig was up and running it seems I had somehow lost my audio driver. I have absolutely no sound now and this is the message I get when I try to adjust the volume :

"No volume control GSStreamer plugins and/or devices found"

Any ideas? Please use noob-friendly language. :)

BTW, my sound card is an AudigySE 7.1

---

### Post by Pirschjaeger on 2007-08-07
I just tried to access Alsa through Terminal and this is what I got:

alsamixer: function snd_ctl_open failed for default: No such device

A little frustrating. :)

---

### Post by Pirschjaeger on 2007-08-07
I tried reinstalling my drivers in Syn Man but it didn't help.

---

