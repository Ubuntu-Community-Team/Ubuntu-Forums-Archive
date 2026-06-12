---
title: "Rhythmbox or XMMS?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2008-03-01
Have been trying and failing to access my local radio station via Rhythmbox. I keep getting the message: 

Couldn't start playback.
You do not have a decoder installed to handle this file.
You might need to install the necessary plugins.

So, to save a lot of hassle i was advised to give "XMMS" a WINAMP look alike a try. Which can play all file formats etc. Could i download XMMS from Synaptic Package Manager and be able to access my local radio station as easy as that?

Would really, appreciate any help and/or advice. Thanks all

---

### Post by Crooksey on 2008-03-01
You are missing the gstreamer plugin required to connect and decode, im not sure on ubuntu, but on Arch i can just install the package set "gstreamer0.10-plugins"..

```

$ sudo apt-get install gstreamer0.10-plugins
$ sudo reboot
```

Should work, if that package set is available.

---

### Post by oscarthefish on 2008-03-01
Hiya Crooksey have tried your suggestion but sadly it didn't work. Thanks for the reply though.

---

### Post by banewman on 2008-03-01
Alot of sreaming radio is only set up for windows media player or realplayer.
The w32codecs should get you listening.
You will need the medibuntu repository enabled for that.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
:)

---

