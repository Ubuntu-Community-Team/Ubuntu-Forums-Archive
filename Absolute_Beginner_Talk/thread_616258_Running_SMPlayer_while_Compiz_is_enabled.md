---
title: "Running SMPlayer while Compiz is enabled"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by tiachopvutru on 2007-11-18
I tried to play video on SMPlayer while Compiz is enabled, and the playback is really choppy. (which doesn't happen when I disable it)  So then, I changed the driver to gl and gl2 (the same problem that was in xv was there as well in x11), it was fixed... or so I thought. The file I was able to play normally was with 640x480 resolution. However, the video lagged behind when I tried to play a video with 1024x576 resolution. Video with 1280x720 just crashed. (not to mention a video with 704x480 resolution softsubbed had ugly sub output)

I'm not sure whether the problem lies in Compiz or SMPlayer (although I believe it more to be compiz, since it doesn't work in sync with some other programs, either), or that my computer is too slow to enabling running both Compiz and playing video at the same time. I can play video fine without Compiz enabled, though.

My system spec is:
AMD Athlon(tm) 64 Processor 3500+
1 GB Memory
ATI Radeon Xpress 200G

I'm currently running Ubuntu Gutsy Gibbon 32-bit


I understand I could have solve it by simply disabling compiz-fusion, but I'm interested in trying dock programs, which require compiz running...

---

### Post by 2ig2ag on 2007-11-18
I think you computer is good enough to play video with compiz enabled. 

I have encountered the same problem.

---

### Post by tiachopvutru on 2007-11-20
<bump>

---

### Post by iura_boss on 2008-07-22
Is your graphic card ATI?

---

### Post by sdowney717 on 2008-07-22
try VLC player and set it to use x11 video.

---

### Post by binbash on 2008-07-22
setting it to use X11 will fix that issue

---

