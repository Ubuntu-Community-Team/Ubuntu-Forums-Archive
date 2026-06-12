---
title: "Multiple video/display problems - out of ideas"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by alchemy101 on 2007-06-22
I have several problems with the display on my ubuntu system. I'll try to be a descriptive as possible, as I know that helps with understanding the problem:
[B]
My system:[/B]
Athlon 64 3500+
Radeon 9550

**Current driver in use: **fglrx (ati driver gives artefacts and doesn't load a lot of stuff)
I have two screens, set up and working fine together.

**The problem:**
[LIST=1]
[*]vlc, Movie Player will always restart the whole system if i attempt to play a dvd or video file on them.

[*]Mplayer will play videos, but only at their native resolution. I can use zoom to enlarge the videos (option in settings), but that causes a lot of lag. 

[*]I can't change desktop effects, with an error stating:
"The composite extension is not available"

[*]I can't view video files at full screen without lag, as well as DVD's. Most applications experience some video lag if I move them around the screen, etc

[*]A side issue, but possibly related, I can't burn DVD's or CD's to completion, with errors around the 77% mark relating to drivers, apparently.
[/LIST]

So put simply, I can't watch movies larger than their native resolution without experiencing significant lag (delay... and lots of dropped frames). Screensavers also lag heaps. Perhaps it's not relevant, but nothing ever lagged under windows environments, so I'm pretty sure the hardware is up to it. For example, the matrix screen saver on ubuntu is very jerky, on XP/Vista it was very smooth.

I'm quite out of ideas. I've tried every driver on mplayer's list, with X11(Ximage/Shm) the only one working. 


BEGGING for some help on this. It's really beyond my experience (only a few weeks into using ubuntu), and these video problems are causing huge difficulties, with the system regularly restarting because of of inability to play video files on all players but mplayer.
[I]
Please, please, please assist me.:([/I]

---

### Post by Obeleh on 2007-06-22
Looks like a driver issue. Try this wiki

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by alchemy101 on 2007-06-22
I get through the whole driver install process with it saying everything is already installed, up to:
sudo aticonfig --overlay-type=Xv

Which crashed my system, and totally stuffed the output from the display. Using recovery mode i restored to my backup of xorg.conf, and it's back to normal again.

So there's evidently an issue here..

---

### Post by alchemy101 on 2007-06-22
I should also note, that if I am watching a DVD or video file, and browsing concurrently, the video will pause momentarily, and the picture and audio experiences a small interruption. 

This is especially obvious if I were to click and drag a firefox window.

---

