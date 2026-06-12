---
title: "MPlayer won't play fullscreen while using s-video to TV"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by digital_sabotage on 2007-04-15
I'm a near noob and am having a minor issue.  When I play movies using MPlayer or VLC on my laptop there are no problems.  I am able to play them fullscreen.  However, if i connect to my TV using s-video out, all display on TV looks fine except any movie I try playing shows just a blue screen (in fullscreen or not).

In MPlayer my video driver in preferences is set at "xv X11/Xv" when this occurs.  If I set my driver to "X11 X11 (XImage/Shm)" then I am able to watch my movie on TV but it will not go fullscreen, only normal size.  I have tried "zoom=yes" in configuration file but then video slows and doesn't keep up with sound.

I run xgl/beryl but this is occuring regardless of regular gnome session or not.  I'm absolutely sold on Ubuntu and have conquered most every issue by reading in these forums.  It's been a fun learning curve ...thanks in advance for any possible fixes I can try:-)

---

### Post by e_james on 2007-04-15
I can't speak for Ubuntu (or Linux generally), but I had a similar problem with Windows. Apparently there are different video principles operating. The general window graphics uses one technique and the movie player image uses another: something called "overlay". In my case I found that I could get full functioning on the TV only if I used the TV exclusively as a monitor. If I attempted to display on both TV and monitor, I only got the window part. It took a bit of trial and error and the procedure may be different with Linux.

---

### Post by digital_sabotage on 2007-04-16
I've tried disabling overlay in vlc to no avail.  Still just get blue screen when output is to tv.  MPlayer I can at least get the vid to play using  X11 (XImage/Shm).  Just not fullscreen.  I recall reading something that led me to believe overlay may be a factor.  I'll try to read and learn a bit more about that.  Thanks for your info:-)

---

### Post by digital_sabotage on 2007-05-04
...fixed ...works fine now with video driver set to gl2 ...i thought i had tried that already  ...i guess not ...or possibly an update fixed ...happy now:-) ..thanks

---

### Post by e_james on 2007-05-05
Thanks for the report. It's nice to know the problem has been solved even if my contribution made no noticeable difference.

---

