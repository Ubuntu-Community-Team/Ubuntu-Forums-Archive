---
title: "Realplayer 10 - where's the firefox plugin ?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-09-13
Realplayer plays radio streams fine but no plugin seems to have been installed for .ram type streams. Tried reinstalling realplayer. Anybody any ideas. I use mplayer plugin for everthinh else.

---

### Post by Maestro23 on 2007-09-13
> **philinux said:**
> Realplayer plays radio streams fine but no plugin seems to have been installed for .ram type streams. Tried reinstalling realplayer. Anybody any ideas. I use mplayer plugin for everthinh else.

Looks like you can use the helix Firefox plugin.  Take a look the this section in the Fesity Guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29)

---

### Post by philinux on 2007-09-13
Yes the helix plugin is the one doing the job on radio streams but there's no plugin set up for .ram type files. I can play them in the external realplayer but where's the plugin?

---

### Post by Maestro23 on 2007-09-13
> **philinux said:**
> Yes the helix plugin is the one doing the job on radio streams but there's no plugin set up for .ram type files. I can play them in the external realplayer but where's the plugin?

Ahh.. misunderstood what you were looking for.  Sorry.

---

### Post by Perfect Storm on 2007-09-13
I don't quiet understand, do you have helix player or realplayer gold?

---

### Post by philinux on 2007-09-13
I installed realplay from synaptic. Helix plugin got installed by realplay.
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.630 built with gcc 3.3.5 on Aug 6 2007

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes

But there is no realplayer plugin for .ram type streams.

---

### Post by Perfect Storm on 2007-09-13
You do have mplayer installed? It could be that it taken its place;

```

RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes

```

---

### Post by philinux on 2007-09-13
I renamed those files mplayerplug-in-rm.so and xpt because it when I clicked a .ram stream the mplayer plugin (replayer 9 plugin) failed to play any stream. I thought installing realplayer 10 would solve the problem. I mean I've got them to play in the external player now.

---

### Post by philinux on 2007-09-13
bump

---

