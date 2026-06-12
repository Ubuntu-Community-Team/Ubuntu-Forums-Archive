---
title: "how to search for a video driver?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Morkhaar on 2007-03-20
hello,
I'm having some problems with the video quality of .avi files (pixelated, low resolution on full screen, especially on dark scenes), on both Mplayer and VLC. I meddled with the video outpout (openGL, default etc) but with no result. 
reading through threads, i suppose that it has to do with my video driver or/and graphics card (sometimes on start up  the ubuntu screen shows up color inverted)
What i should do is to find out if my driver is the most up to date, and try to install a new one (?). 
The problem is that, being a complete newbie, I have no idea on how to find out.. 
and furthermore, I don't have the slightest idea on what type of update i should be searching for... :-k 
could somebody please enlighten me on the matter?

i'm using ubuntu 6.06 on a VAiO VGN-FS115Z, 128 MB nvidia GFGo 6200

---

### Post by NT4usB on 2007-03-20
Have a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)
Then grab Envy and it will install the latest.
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Morkhaar on 2007-03-20
thanks for the tip, i'll look it up!

---

### Post by steve101101 on 2007-03-20
would you say the colors look funk and all multi colored. you may need to change the color depth to 16 instead of 24 bits. 

try this

```

sudo gedit /etc/X11/xorg.conf

```

then change the DefaultDepth 24 to 16 then save. 

press <ctrl>+<Alt>+<Backspace> to restart  X.

---

### Post by Morkhaar on 2007-03-20
well on the start up screen yes, i could say it looks funky!(but only happens once in a while)
playing video has more of a 'skanner darkly' feel , a bit cartoony (can't explain it better!), the pixels are so big that feels like you edited the image using photoshop filters. haven't tried yet the color depth, thanx anyway

---

### Post by Morkhaar on 2007-03-20
nope. the default depth is already 16. Damn! for a while i thought i could get away without reading all the 81 pages of the thread..

---

