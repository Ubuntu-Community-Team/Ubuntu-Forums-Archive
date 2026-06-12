---
title: "Xgl causes green lines at the top of videos in VLC"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by lian1238 on 2007-12-02
I started getting this green line in VLC player a while back and I didn't know what was causing it, until now. The answer was xgl. I was uninstalling and reinstalling xgl and comparing the quality of window switching effects. (xgl vs non-xgl?) While I had xgl uninstalled, the green thick line at the top of some videos played in VLC was *gone*. I reinstalled xgl and the green line was *back*. The line is about 20 px thick.

Is this a known issue? The output module I use in VLC is XVideo.

I would just have xgl uninstalled, but then my playing music stops a while when I'm sliding the windows with the shift-switcher effect but with xgl, no problem. Also, I get a black-screen "blink" once in a while without xgl. On the other hand, xgl renders(?) the windows in lower quality.

How can I fix the green line problem? And also, if anyone could tell me how I can configure(?) xgl to render the windows in higher quality?

(note: green line only appears on *some* videos and only with VLC if they do.

---

### Post by GGLucas on 2007-12-02
I had the same problem, I uninstalled xserver-xgl because I didn't need it anyway, but before I figured out it was caused by that, I found out that the lines were not there when I used the (non-GUI, terminal command) mplayer command to play the videos.

---

### Post by nothumphrey on 2007-12-09
finally... an answer.  try this one :)

[http://ubuntuforums.org/showthread.php?t=446673](http://ubuntuforums.org/showthread.php?t=446673)

---

