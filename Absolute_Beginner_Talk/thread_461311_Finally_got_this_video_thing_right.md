---
title: "Finally got this video thing right"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by icelechi on 2007-06-01
Hi,
I used to have trouble with getting videos to play in Firefox but I think I finally got it. I found that mozilla-mplayer was the best plugin for videos unfortunately, it conflicted with Real Player's plugin. Whenever a Real media video was to play, mplayer would start up instead. 

Well to sort this out, you can simply go to /usr/lib/firefox/plugins/ and delete the mplayerplug-in-rm.so file. Also if you are using Ubuntu 7.04 (Feisty), totem plugins were placed in this folder as well. Go ahead and delete them also.

If this does not work for you, you can replace the totem and mplayer files by copying and pasting the following command in the terminal:

sudo ln -s /usr/lib/totem/lib* /usr/lib/firefox/plugins/ && sudo ln -s /usr/lib/mozilla/mplayerplug-in-rm.so /usr/lib/firefox/plugins/

I am so stoked that I finally got this to work. Hope it works for you too :)

---

