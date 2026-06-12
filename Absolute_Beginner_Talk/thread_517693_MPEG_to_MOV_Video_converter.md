---
title: "MPEG to MOV Video converter"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by guitarman on 2007-08-04
Hi,
I recently purchased a SanDisk Sansa e250 MP3 player with video.  It comes with its own media converter software (but it's in Windows XP!).  I am trying to convert an MPEG video to MOV format since this is the format the Sansa recognizes.  I am trying to find a media converter that runs on Ubuntu.  

Some other threads mentioned DeVeDe and the Mencoder, but they don't seem like the right ones for me.

Any suggestions.

thanks

---

### Post by apswartz on 2007-08-04
Take a look at avidmux and see if it might suit you.

---

### Post by bogolisk on 2007-08-04
> **guitarman said:**
> Hi,
I recently purchased a SanDisk Sansa e250 MP3 player with video.  It comes with its own media converter software (but it's in Windows XP!).  I am trying to convert an MPEG video to MOV format since this is the format the Sansa recognizes.  I am trying to find a media converter that runs on Ubuntu.  

Some other threads mentioned DeVeDe and the Mencoder, but they don't seem like the right ones for me.

Any suggestions.

thanks

The *mov* is just the container format in this case it's likely Quicktime. Apparently the codec it supports is a type of mjpeg. You'll have to experiment with different encoding parameters :

     mencoder -ovc lavc -lavcopts vcodec=mjpeg:.....

see this:

[http://www.visi.com/~grante/sansa/](http://www.visi.com/~grante/sansa/)

---

