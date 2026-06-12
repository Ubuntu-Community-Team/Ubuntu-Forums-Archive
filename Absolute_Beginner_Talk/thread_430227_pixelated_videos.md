---
title: "pixelated videos"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by cf1709 on 2007-05-01
why do the videos played on my ubuntu pc appear pixelated when stretched to full screen? i doesn't happen in windows though... a stupid problem of mine...

if it's something to do with my graphics chip, then i would like to tell that it's a "unichrome igp pro" graphics chip. i hope somebody can help

---

### Post by Angry_Man on 2007-05-02
A few questions:

How bad would you rate the pixelation, from 1 (slightly pixilated) to 5(extremely blocky, unwatchable)?
Are you using Totem (the default media player) or a different package for video playback?
What video card do you have?
What video card driver are you using?
Have you made any changes to the default graphical configuration (e.g. Enabling desktop effects, using XGL instead of Xorg, etc)

---

### Post by Steve H on 2007-05-02
From personal experience I have found that VLC is quite good at producing good quality playback. I did have "blocky" output for a while but I found that playing around with the "Video Output" setting in VLC helped enormously. It now looks as good as XP.

Hope that helps.

:)

---

### Post by cf1709 on 2007-05-03
@Angry_Man

I guess its 2 or 3 since I can't read the subtitles
I usually use vlc for playback.
It is an motherboard-integrated chip named "UniChrome IGP Pro"
I don't know the driver. Sorry...
I didn't change anything, not even the background,resolution,themes

@Steve H

Please help me on how to tweak the settings in vlc. thanks

---

### Post by Steve H on 2007-05-03
Ok, I'm not at home so I'll have to try and remember......here goes

Open VLC
find "Settings" or "Preferences"
Tick the "Advanced" box
Find "Video"
Find "Video Output"
If you look around there you will find "Video output codec" or something similar, try using OpenGL or X11, have a play around with them. I find OpenGL gives better playback but will not stream from the internet, X11 streams but is a bit blocky on fullscreen.

Good hunting, Let me know how you get on!

:)

---

