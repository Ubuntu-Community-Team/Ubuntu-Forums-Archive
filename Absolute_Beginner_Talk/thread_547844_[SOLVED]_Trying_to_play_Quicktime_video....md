---
title: "[SOLVED] Trying to play Quicktime video..."
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-09-10
I'm trying to watch a Quicktime trailer, and this is the message I'm getting when it opens up the mPlayer:

Error opening/initializing the selected video_out (-vo) device

Any ideas?

---

### Post by philinux on 2007-09-10
Try again but this right click in the player and select configure, have a look at what is checked and unchecked.

---

### Post by Paulmd on 2007-09-10
> **cwrann said:**
> I'm trying to watch a Quicktime trailer, and this is the message I'm getting when it opens up the mPlayer:

Error opening/initializing the selected video_out (-vo) device

Any ideas?

This was a major hassle for me to get working. I eventually settled on VLC. Also, to play them in the browser, uninstall the totem and mplayer mozilla plugins, and use vlc's plugin instead.

---

### Post by Perfect Storm on 2007-09-10
> **cwrann said:**
> I'm trying to watch a Quicktime trailer, and this is the message I'm getting when it opens up the mPlayer:

Error opening/initializing the selected video_out (-vo) device

Any ideas?


Try change it to video drivers to xv (mplayer preferences).

---

### Post by cwrann on 2007-09-10
I changed the video diver to xv. I noiw get a choppy video and numerous error pop ups all telling me:
"Alsa control: Unable to find simple control 'PCM',0"

---

### Post by philinux on 2007-09-10
Mine is set to X11 and no probs. Got rid of totem plugin I just use mplayer

---

### Post by cwrann on 2007-09-21
It looks like I had a couple of things going wrong. I got rid of the VLC plugin, I installed gstreamer gl from synaptic and I got rid of media player connectivity. 
I think that Media Player Connectivity was not allowing the computer to buffer the video clips far enough out to make them watchable, and wasn't saving them in temporary files so that I could wait for the entire clip to load before viewing.
Without Media Player Connectivity the browser was shutting down when I tried to play QT, presumably, because I had VLC selected for quicktime files but mplayer set as the prefered overal media player.
or maybe it was all because I didnt have gstreamer gl installed.

---

