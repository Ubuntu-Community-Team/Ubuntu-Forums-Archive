---
title: "Firefox Media Player problems in Gusty"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by lduplantie on 2007-10-23
If Ubuntu wants to have a better adoption rate, I suggest that they fix the media player issues in Firefox. The Totem Firefox plugin plainly just does not work for Window Media streaming video. I do not have the latest hardware (P3-1GHz-512M RAM, Intel 82815 on board video) and do not want to spend more H/W $. I have no problems with Flash based content.

I have tried to install other players (VLC, Xine) with no success. I sometimes get that my i386 H/W is not supported.

Any simple and fast suggestions to fix this problem?

Thank you

Laurent

---

### Post by philinux on 2007-10-23
Just go to synaptic and uninstall the totem-mozilla plugin and then install the mplayer plugin.

---

### Post by Seisen on 2007-10-23
Try mplayer and the mplayer plugin

```
sudo apt-get install mplayer mozilla-mplayer
```

---

### Post by lduplantie on 2007-10-23
I did a clean install of gusty yesterday. "apt-get" cannot find mplayer!

Any idea where I can find it?

Laurent

---

### Post by drs305 on 2007-10-23
Make sure the multiverse repository is enabled. The GUI way to do this is System, Administration, Software Sources, Ubuntu Software, and make sure multiverse is checked.

You can get to the same place via synaptic, settings, repositories...

---

### Post by trjnhrse44 on 2007-10-23
enable the backports in system, admin, software sources.
(Just check all the boxes for available repos, and updates.)

Totem G-streamer should play the video too, try downloading a wmv and playing in totem from the desktop, you may just need to let the system install the codecs.  This isnt done when you open a streaming video in firefox, you need to do it first from a local file.

Alternatively you can add the codecs through add/remove software, just search for Gstreamer and enable the extra plugins and the ffmpeg plugins.

---

### Post by trjnhrse44 on 2007-10-23
drs beat me to it.. heheh same thing tho

---

### Post by lduplantie on 2007-10-23
I keep getting problems.

I can't install mplayer (seems to conflict with totem, removed totem, says its missing librairies, skins, etc.)

Re-installed totem, wanted to install extra codecs (per trjnhrse44 suggestion) Synaptic or Add/Remove says my machine (i386) is not supported. Never had that problem with 7.04.

Any clues about what is going on?

Laurent

---

### Post by feldhege on 2007-10-23
Well At least you got totem to re-install. After removing it, trying to get mplayer to work, and then trying to reinstall it, it says Movice Player can't be installed on my type of computer (i386). Now what?

Robb

---

### Post by alienexplorers on 2007-10-24
If mplayer does not work try for firefox the extension MediaPlayerConnectivity which is located at:
> [https://addons.mozilla.org/en-US/firefox/search?q=mediaplayer&status=4](https://addons.mozilla.org/en-US/firefox/search?q=mediaplayer&status=4)

---

