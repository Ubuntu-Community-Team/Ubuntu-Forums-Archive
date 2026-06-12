---
title: "Music Decoders"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by tjbenson on 2007-03-03
I am a newbie to Linux but love it so far.  I am trying to play an Internet radio station in Rhythmbox 0.9.6 but keep being prompted with the following:  
"You do not have a decoder installed to handle this file. You might need to install the necessary plugins."  Anyone know what plugins they are referring to and where I can download them?  And, how do I install them?  Thanks!

---

### Post by luke411 on 2007-03-03
[http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

That will take you to the Gstreamer web site where you can read and download all of the plug ins that cannot be included for legal reasons. You will also find the ones you need for playing mp3, mp4, dvd'd etc. I basically grew tired of reading them and installed all of the ones that looked good until everything worked. I had no ill effects from that strategy but to each his own.

---

### Post by tjbenson on 2007-03-03
Thanks!  I'll give that a try.  That strategy sounds like one I'd employ as well.  Thanks again.

---

### Post by Prometheus.172214 on 2007-03-03
Give VLC a try. Works quite well for me.


Install VLC Media player in Ubuntu

You need to make sure that you have a &#8220;universe&#8221; mirror in your /etc/apt/sources.list

Open a Konsole and type in:

sudo apt-get update

sudo apt-get install vlc vlc-plugin-esd

This will complete the installation

If you want to open VLC You need to go to Applications&#8212;>Sound&Video&#8212;>VLC Media Player

---

### Post by AndyCooll on 2007-03-03
See the "Restricted Formats" link in my signature. That will get you up and running.

:cool:

---

