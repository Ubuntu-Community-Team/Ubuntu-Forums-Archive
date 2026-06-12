---
title: "audio files in Firefox or..."
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by mackinax on 2006-03-21
I need to install a plugin or whatever so I may play audio files within Firefox.
(Or even just an external program that I could drag-n-drop the links to would be fine...)

Specifically, I require the ability to play windows media asx files, because I would like to preview music samples on sites like allmusic and amazon.

This is what I have installed -

Ubuntu Breezy 5.10 (gnome)
Firefox 1.5.0.1
VLC 0.8.4
Mplayer GUI dev-CVS--4.0.2 
Totem (gstreamer) 1.2.0
Beep Media Player 0.9.7
XMMS 1.2.10
Rhythmbox 0.9.0

Thank you,

---

### Post by IYY on 2006-03-21
There is a package called "mozilla-mplayer" which plays media in Firefox. I'm not 100% sure if it plays the specific filetype you asked for, but you should try.

**sudo apt-get install mozilla-mplayer**

---

### Post by krusbjorn on 2006-03-21
If you'd rather have embedded video/audio files play in an external media player of your choice, try the MediaPlayerConnectivity extension for Firefox. It's great.

---

### Post by mackinax on 2006-03-21
[QUOTE=IYY]There is a package called "mozilla-mplayer" which plays media in Firefox. I'm not 100% sure if it plays the specific filetype you asked for, but you should try.[/QUOTE]
I installed it via Synaptic. But it didn't seem to be integrated by Firefox. All I see in "about: plugins" are Flash/Shockwave and Null. Perhaps it is because my firefox is 1.5, or did I miss a step?

[QUOTE=krusbjorn]If you'd rather have embedded video/audio files play in an external media player of your choice, try the MediaPlayerConnectivity extension for Firefox. It's great.[/QUOTE]Thanks, I will look into this next.

---

### Post by mackinax on 2006-03-21
[QUOTE=krusbjorn]MediaPlayerConnectivity extension for Firefox[/QUOTE]
With this extension, I was able to get wma/asx links from amg and amazon to load in VLC player.
Thanks!

---

