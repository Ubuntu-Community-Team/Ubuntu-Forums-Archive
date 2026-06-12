---
title: "Brasero codec ?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2008-04-17
Tried to burn an audio cd,and it says "unhandled song, can't be handled by gstreamer,make sure you have the proper codec installed". Which codec do I need ? It doesn't say. :confused: Thanks

---

### Post by freduardo on 2008-04-17
I guess that depends on what type of file (or files) you're trying to make an audio cd of.
e.g. if it's an .mp3 file you'll need codecs for .mp3

Check this to make sure you have the proper codecs installed:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by heymae on 2008-05-06
I had the same problem but it is now, thanks to jem, easily solved.

In Hardy synaptic manager and add/remove you will discover a small package called DeVeDe, install that and your problems are over.

Directions: Using DeVeDe convert your movie file to ISO ... Then hit the Burn ISO button in Brasero ...You can then watch a good quality DVD on TV.

---

### Post by mechgt on 2008-05-30
In order to add mp3's, I added 'gstreamer0.10-plugins-ugly', restarted Brasero and started burning.  My computer apparently didn't have an mp3 decoder on it prior to this, as it wouldn't play mp3s either.

Hope this helps someone!

---

