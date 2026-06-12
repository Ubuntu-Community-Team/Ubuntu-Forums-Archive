---
title: "optimal video codecs and players"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by rockstar on 2008-04-05
I cant decide which formats to use.  I've already tried MKV.  I tried to custom compile a video player with Smplayer, VLC and Xine.  Here are my options to start from scratch, any suggestions?

Set output format (avi/mp4/ogm/mkv, default:
                            autodetected from file name)

Set video library encoder (ffmpeg,xvid,
                            x264,x264b13,x264b30 default: ffmpeg

 Audio encoder (faac/lame/vorbis/ac3/aac+ac3) 
                            ac3 meaning passthrough, aac+ac3 meaning an
                            aac dpl2 mixdown paired with ac3 pass-thru
                            (default: guessed)

---

### Post by remali on 2008-04-05
I use vlc player that plays anything without needing downloading codecs...
You might need though to put ouput modules in X11 or opengl (if u think X11 is pixelated)

---

### Post by steveneddy on 2008-04-05
Yes - VLC is a wise choice.

---

### Post by bumanie on 2008-04-05
+1 Vlc plays just about any video codec in existence.

---

### Post by stefangr1 on 2008-04-05
I use mplayer-svn, compiled from source to get that few %'s additional performance gain. I use it without gui and don't run in in a terminal, to prevent this "to many packages" error messages frustrating playback (this happens with some x264 1080p videos that are on the edge of being just playable or just not playable).

After doing a lot of experimenting I find this the best solution for watching x264 HD movies, all other stuff can usually be played with virtually every player assuming that the right codecs are installed.

---

### Post by D|F on 2008-04-05
How can i install xine player?
i try to install xine player, but the result is like this.

sudo apt-get install xine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine has no installation candidate

---

### Post by stefangr1 on 2008-04-05
sudo apt-get install xine-ui

---

