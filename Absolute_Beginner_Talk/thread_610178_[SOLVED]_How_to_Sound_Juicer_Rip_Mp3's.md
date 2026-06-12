---
title: "[SOLVED] How to: Sound Juicer Rip Mp3's"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-11-11
Just installed Ubuntu 7.10 and I would like to rip some of my CD's
into mp3 using sound Juicer.... How do I do this.
I have tried to choose MP3 but it always reverts back to the default
choices. I know I had to install libmp3lame.so.0 in Audacity.
Is there something I need for Sound Juicer?

---

### Post by Orbital75 on 2007-11-11
Do I need to install some Restricted Codec package or something?
I've been told it's possible but just don't know how to set it up.

---

### Post by bgast1 on 2007-11-11
I prefer FLAC, because it is Lossless. But you can do MP3 if you like. Open up Sound Juicer, click on Edit, then go to Preferences and you should be able to figure out from there. I am absolutely new to this Linux thing and I had no trouble figuring it out. Once you have your preferences set just hit extract and that's all there is to it. :guitar:

---

### Post by Orbital75 on 2007-11-11
Tried that and it didn't work.... I think I may need some codes, Plugins, something.....

---

### Post by ericesque on 2007-11-19
I'm not seeing this either...

---

### Post by kpkeerthi on 2007-11-20
Do not forget the "search" feature. And there is Tutorials and Tips section in this forum. Here are a few I found for you...

[http://ubuntuforums.org/showthread.php?t=295698](http://ubuntuforums.org/showthread.php?t=295698)
[http://ubuntuforums.org/showthread.php?t=22010](http://ubuntuforums.org/showthread.php?t=22010)
[http://ubuntuforums.org/showthread.php?t=957](http://ubuntuforums.org/showthread.php?t=957)
[http://ubuntuforums.org/showthread.php?t=99115](http://ubuntuforums.org/showthread.php?t=99115)

---

### Post by doncristobal on 2007-11-23
I had the very same problem although i was following the instructions in the desktop guide. Then I found the (a?) solution: I had to get gstreamer0.10-plugins-ugly-multiverse (GStreamer plugins from the "ugly" set (Multiverse Variant)), restart sound juicer, voilà. 
See [http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

---

### Post by nick_h on 2007-11-23
The codecs you need are listed on the [Restricted Formats](https://help.ubuntu.com/community/RestrictedFormats) wiki page.

The Sounder Juicer configuration for mp3 can be found on the [CD Ripping](https://help.ubuntu.com/community/CDRipping) page.

---

### Post by Ossus on 2007-11-24
I found the easiest way was to search the add/remove programs for "lame" which will bring up the restricted package. Installing that should allow sound juicer to rip MP3s

---

### Post by Orbital75 on 2007-12-13
I solved this by installing the ugly plugins.
Thanks guys for the help, she works great
now.

---

