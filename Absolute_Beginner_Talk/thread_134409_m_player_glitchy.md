---
title: "m player glitchy"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2006-02-21
M player is quite glitchy when streaming video (.mpeg or .wmv) Is there anyway to fix this?  I installed all my plugins and drivers w/ automatrix

Thanks!

Donald

---

### Post by sharke on 2006-02-22
edit /etc/mplayer/mplayer.conf add the following to the bottom of the file:

srate=48000
Regards
Sharke

---

### Post by inovermyheadd on 2006-02-22
hey thanks sharke,

The video is good, but now the audio is way out of sync...what now?:)

---

### Post by inovermyheadd on 2006-02-22
nm, it isn't out of sych, It seems to load the audio more quickly than the video...then when the video starts, the audio starts again...hehe, weird eh?

---

### Post by sharke on 2006-02-23
Try adjusting the srate try 24000
Regards
Sharke

---

