---
title: "Capture Video from web"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-08-02
Is there a way to capture video from a website and convert it somehow to burn it to a cd? As in, capture video from tvlinks or something and burn it to a cd?

---

### Post by mcduck on 2007-08-02
Sure. Actually there are many ways. For flash videos, you can just copy the file from /tmp and then use ffmpeg2theora to convert it from .flw into .ogg.

DivX videos and all other videos that are opened with mplayer-plugin can be usually saved from the player's right-click menu after the video has been fully downloaded.

There are also man Firefox extensions for saving video content from web pages.

---

### Post by ukulele_ninja on 2007-08-02
i opened gedit /temp but its an empty file! Where do I see the flash file I downloaded?

---

### Post by atomkarinca on 2007-08-02
in ~./mplayer/firefox directory there should be one directory (the name may differ). videos should be in the Cache directory.

and you can use videodownloader for flash videos (the easy way): [https://addons.mozilla.org/en-US/firefox/addon/2390](https://addons.mozilla.org/en-US/firefox/addon/2390)

---

### Post by ev5unleash1 on 2007-08-02
I know firefox has extentions to do such things. And if you are running Windows or a virtual version of iit you can get real player from Real.com. It will allow you when you hover over a flash video to download it and then you can use spasific software to convert it. But most good software costs money to do such a thing.

---

