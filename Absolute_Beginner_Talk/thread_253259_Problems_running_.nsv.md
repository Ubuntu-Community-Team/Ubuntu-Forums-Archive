---
title: "Problems running .nsv"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by absolutenewbie on 2006-09-08
Ok so i'm trying to watch this streaming TV link at [http://www.no-sry.net:9000/;stream.nsv](http://www.no-sry.net:9000/;stream.nsv) but I can't seem to cut it. I've tried in totem, VLC, and mplayer, but each one fails. After a little lurking I found out the player of choice is mplayer, and this error is usually due to codec problems, but i updated my codecs so i know they are up to speed. 

Anyway when i plug the link into mplayer i get the error "Cannot find codec matching selected -vo and video format 0x32365056" Most of this is jibberish to me but i understand cannot find codec, but my win32 codecs are all update! I just checked them. So i go into terminal and try it out and holeeh crap i am bombarded by error. I input mplayer [http://www.no-sry.net:9000](http://www.no-sry.net:9000) and get back a stream of "FAAD: error: Unexpected Channel configuration change, trying to resync!" Over and over and over again.

Any help?

---

### Post by orb9220 on 2006-09-08
.nsv is a restricted format exculsive used by winamp music video's. It is very diffcult to find players in windows to play these alone linux playing them.

The only thing I can think is to google linux .nsv and see what pops up.

---

### Post by crispy_420 on 2006-09-08
I did a quick search of google and found this:

[http://gentoo-wiki.com/HOWTO_NSV_on_Linux](http://gentoo-wiki.com/HOWTO_NSV_on_Linux)

Here is one from winamp forums:

[http://forums.winamp.com/showthread.php?s=&threadid=149214](http://forums.winamp.com/showthread.php?s=&threadid=149214)

It all looks like it comes down to the right player and the right codec.

---

### Post by CarpKing on 2006-09-20
I have tried repeatedly to watch the same stream (I have all the codecs that I know of installed).  In VLC, the sound works, but not the video (as long as I set it to "stream output" and select the mp4 option), while in mplayer I can watch the video if I start it from the commandline with -nosound.  If I just use mplayer, I get the endless stream of FAAD errors that absolutenewbie was talking about.   The video and sound together play for about half a second, then the program freezes.  I'm using mplayer and VLC from the repositories; I've looked into the VLC side of things and found that it does not currently support the VP6 codec that this stream uses.

---

