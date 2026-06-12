---
title: "amarok problem"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Bigguy2468 on 2006-09-09
Here's one for you.
I have 2 machines that I loaded ubuntu 6.06 onto.
The first one plays music from Shoutcast.com using amarok right out of the box so to speak.
The second ones doesn't. However, the one that is not playing the music will show the url in the playlist, the count down timer for the song works and the titles of the song come up for each one, there's just no sound.
Also, the graphical equalizer that usually bobs up and down isn't showing that music is playing either. I have sound for other things so it can't have anything to do with the sound card from what I can tell.

I'm baffled!

Any suggestions?

---

### Post by jordanmthomas on 2006-09-09
Maybe you need to install the mp3 codecs since shoutcast streams as mp3?  Couldn't hurt, I don't reckon.

---

### Post by Bigguy2468 on 2006-09-10
> **jordanmthomas said:**
> Maybe you need to install the mp3 codecs since shoutcast streams as mp3?  Couldn't hurt, I don't reckon.

I installed the following batch of codecs:

gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gxine
libxine-main1
libxine-extracodecs
w32codecs

Now it seems to be working.

---

