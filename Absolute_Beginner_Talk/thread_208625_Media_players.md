---
title: "Media players"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by jbm222 on 2006-07-03
Ok, I've had all of my media files sucessfully playing in some media player using either xine  or gstreamer at some point.  But never all of them at the same time.  I need to be able to play mp3, wma, ogg, m4a (these seem to be the hardest, but i have had them working), and .wav files all with a single media player.  Preferably XMMS.  And I would like streaming audio to work in Firefox at the same time.  I've messed around with gstreamer and xine, mplayer, totem, rythmbox, xmms so much that I can't remember what worked under what setup.  

I know i've had better luck with xine, and that mozilla-mplayer works better than the totem firefox plugin (which gives endless amounts of errors).

But is there be a setup that will work for ALL of my media playing needs?

---

### Post by woedend on 2006-07-03
xmms with play all of those filetypes.  
I have a .deb specifically for WMA with xmms if you want it.  xmms-mplayer will also work with WMA's, however.  as for m4a, theres also an xmms plugin for that in the repos(must have universe and multiverse repos enabled), search for xmms-
so the question is...do you want one program to do EVERYTHING or one for video and one for audio?  You can get xmms to play videos via mplayer plugin, but its featureless.

---

### Post by Perfect Storm on 2006-07-03
You should properly go for VLC then if you want everything in one.

---

### Post by macmelvyn on 2006-07-04
This looks like a topic to put me right, can anybody help me associate firefox correctly so that I can listen to a WMA audio stream from lbc.co.uk ?
I have read enough pages to sink the preverbial battleship!!
Also the best appliation tip for Audio would add spice to the whole thing, I must have installed and uninstalled every possible permation of multi-media there is!!
Still I get Totem reporting WMA errors, though they do seem to vary a bit.
Thanks in anticipation
MacMelvyn

---

### Post by Perfect Storm on 2006-07-04
You should properly try with mplayer, just remember to install w32codecs.

---

### Post by AndyCooll on 2006-07-04
Xine and gstreamer are usually the backend "engines" of other media players (though there is a frontend to Xine too). Amarok for instance uses either the gstreamer or xine engines.
Mplayer and VLC also have their own engines.

As Artificial Intelligence says, you should probably use VLC if you want one app fits all approach since it has a Firefox plugin too.

I usually just get Automatix to install all my media codecs. What I then usually end up with is using Totem for most of my movie clips, Amarok/Listen for my audio files, and mplayer has been installed as my browser plugin.

:cool:

---

### Post by Jagot on 2006-07-04
I use Rhythmbox to play all of those file types.  Providing you inall the correct codecs - the gstreamer ones in the repos and w32 codecs, you can play all of those file types in it.

---

### Post by barbarian on 2006-07-04
amarok

---

