---
title: "[SOLVED] How do I set a video as the desktop wall paper?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2007-12-03
Like this guy does in his video:
[http://youtube.com/watch?v=bYsxaMyFV2Y](http://youtube.com/watch?v=bYsxaMyFV2Y)

---

### Post by jordanmthomas on 2007-12-03
He probably is using xwinwrap.
[http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/](http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/)
You can use this link to help you out.  Obviously, you'll want to replace the screensaver's commands with mplayer.

---

### Post by piratesmack on 2007-12-03
So I'd have to convert a video to a screensaver?

---

### Post by jordanmthomas on 2007-12-03
No, instead of running a screensaver under xwinwrap you'd run "mplayer filename"

---

### Post by piratesmack on 2007-12-03
sorry
so what exactly is the command. My username is steven and the video is on my desktop, named d.avi

I'm not sure where to put the "mplayer" in the command

---

### Post by jordanmthomas on 2007-12-03
```
xwinwrap -ni -argb -fs -s -st -sp -nf -b -- "mplayer ~/Desktop/d.avi" -window-id WID
```
should do it, assuming you've installed xwinwrap.

I forgot to mention earlier though that xwinwrap has some issues if you use AIGLX.  It works fine with XGL though.

---

### Post by piratesmack on 2007-12-03
Hmm I get:
mplayer ~/Desktop/d.avi: No such file or directory
mplayer ~/Desktop/d.avi died, exit status 2

But the file does exist.

Thanks for your help, though

---

### Post by jordanmthomas on 2007-12-03
Does the command
```
mplayer ~/Desktop/d.avi
``` work on its own (not in the xwinwrap line)?
If so, you may need to make a script and put it in the xwinwrap line instead like so:
```
gedit ~/vidwallpaper
```
put this in there:
```
#!/bin/bash
mplayer ~/Desktop/d.avi

```
then, 
```
chmod +x ~/vidwallpaper
```
and change your xwinwrap command to this:
```
xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /home/steven/vidwallpaper -window-id WID
```
Lastly, it may be necessary for you to put this in your mplayer command (it is for me anyway)
...something like
```
mplayer [COLOR="Red"]-vo x11[/COLOR] filename
```

---

### Post by jordanmthomas on 2007-12-03
Also, if this doesn't work out, vlc can set your wallpaper to be a video.

---

### Post by piratesmack on 2007-12-03
I got it working!
Wow it's amazing. I have a movie set as my desktop wallpaper, a million 3d effects, and it's still using less resources than Vista.

---

