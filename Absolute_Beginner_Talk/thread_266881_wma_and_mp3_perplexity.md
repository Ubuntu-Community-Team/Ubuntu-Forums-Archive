---
title: "wma and mp3 perplexity"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Boatswain on 2006-09-27
Hey all!  So I'm having some problems with media players.  I've been mostly using XMMS for music lately, and it's working with MP3s just fine, no problems at all.  It can at least figure out the titles of any WMAs I try to make it play, but can't seem to read any content and will just cycle through a playlist full of them as though I had just asked it to play a bunch of songs of no duration.  I've been using Totem just for DVDs, but just the other day I was curious and tried to make it play some WMAs--no problem, and ditto with MP3s.  So next I start checking out other media players (Rhythmbox and Exaile, in particular) and they can't play anything but my few OGG files.

So what exactly is going on, and how do I get Exaile or XMMS to play all my formats?

Thanks!

---

### Post by cptjaben on 2006-09-27
what engine are you using, xine or gstreamer or... You probably need to install codecs for other formats such as FLAC, Ape, and OGG. I found [this]("https://help.ubuntu.com/community/RestrictedFormats") page to be somewhat helpful when I was installing audio codecs.

---

### Post by Boatswain on 2006-09-28
Hey thanks, that did it nicely.  Don't know how I managed to not notice that xmms  isn't gstreamer, and that totem is xine...  Cheers!

---

