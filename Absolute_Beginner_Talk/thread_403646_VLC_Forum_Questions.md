---
title: "VLC Forum Questions"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-04-07
I have scanned forum after forum and stil not found a way to make VLC default. There must be a clear method for edgy 6.10. If there is I would like to know about it. I can not play certain things on Bloomberg or CBS the Young and the restless. VLC never pops up like it should. Nor does it pop up on Amazon.com music listening.
Ross

---

### Post by moffa on 2007-04-08
If you are talking about for in firefox:

Remove the package totem-mozilla and install the package mozilla-plugin-vlc

---

### Post by rosswmcgee on 2007-04-08
That is done and in both Bloomberg and CBS Innertube, VLC pops up but there is no audio or video. I guess I am part way there but need some other change. Thanks for the reply. Ross

---

### Post by moffa on 2007-04-10
I think you need to install a bunch of codecs.  I was trying to help another person with Quicktime, but they didn't get it working either.

---

### Post by Hallvor on 2007-04-10
VLC uses its own codecs. You could always try updating VLC if you have an older version than 0.8.6a. Instructions are on [www.videolan.org](www.videolan.org)

Have no idea if it works, but it is worth a try.

---

### Post by rosswmcgee on 2007-04-10
have vlc 8.6, I  think perhaps cbs only allows real time and windows media player. I give up. The rest of EDGY is fine.

---

### Post by moffa on 2007-04-12
I checked the CBS website and they use RealPlayer.

A quick google turned up RealPlayer for linux:
[http://www.real.com/linux/?src=](http://www.real.com/linux/?src=)

edit:  they recommend you use the helix player

```
 sudo apt-get install helix-player mozilla-helix-player
```

---

### Post by rosswmcgee on 2007-04-12
> **moffa said:**
> I checked the CBS website and they use RealPlayer.

A quick google turned up RealPlayer for linux:
[http://www.real.com/linux/?src=](http://www.real.com/linux/?src=)

edit:  they recommend you use the helix player

```
 sudo apt-get install helix-player mozilla-helix-player
```
I already have real player installed. Can you get CBS to work?
 I did figure out how to do the Bloomberg video talking heads. Open the video, vlc opens up right click on the video/select media connectivity/ scroll down to the vido stream and click on  it then it opens. some have no sound though others do, why I don't know.

---

### Post by Michaelt74 on 2007-04-12
Check out the post by mgmiller, it shows you how to configure VLC to make it the default player.

Good luck!

---

### Post by Michaelt74 on 2007-04-13
Apologies, here is the post

[http://ubuntuforums.org/showthread.php?t=326591](http://ubuntuforums.org/showthread.php?t=326591)

---

