---
title: "Sound issues with Fresh install of Ubuntu 18.04.4 LTS on Macbook Pro 13&quot; 2017"
date: 2020-02-24
forum: Apple Hardware Users
---

### Post by darrenjkt on 2020-02-24
I've dual booted my Macbook Pro with Mac/ Ubuntu. On a fresh install, Ubuntu does not have sound coming out of my macbook speakers. I've tried every solution I could find on the web but to no avail. 

I have tried
- Alsamixer: muting and unmuting each channel
- Pavucontrol: changing the configuration settings
- sudo alsa force-reload
- Removing pulse directory so that it'll be freshly created on reboot
- Edited the speech-dispatcher file to change RUN=yes to RUN=no
- Reinstalling alsa-base and pulseaudio

```
[COLOR=#c20cb9]**sudo**[/COLOR] apt remove [COLOR=#660033]--purge[/COLOR] alsa-base pulseaudio
[COLOR=#c20cb9]**sudo**[/COLOR] apt [COLOR=#c20cb9]**install**[/COLOR] alsa-base pulseaudio
```

I'm not too sure how to fix this issue. Can someone help me?

---

### Post by wildmanne39 on 2020-02-24
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

