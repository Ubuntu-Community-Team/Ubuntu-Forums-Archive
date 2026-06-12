---
title: "gst-launch produces &quot;jumpy&quot; ogg"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by lhomme on 2008-01-21
I made a simple script a long time ago to convert non-DRM'ed wma to ogg using gst-launch.  At some point for reasons unknown it started producing "jumpy" (see links at end) ogg vorbis files.
I realize there are other things I could do the converting with, I just would like to know what's wrong with what I'm doing.

this is the important part:
```
for i in *.wma; do
	 gst-launch-0.10 filesrc location="$i" ! decodebin ! audioconvert ! vorbisenc ! oggmux ! filesink location="$i".ogg
```
(at one point I had 'audioresample' in there after audioconvert because I had seen it in several examples, it didn't change the result)

the trouble doesn't seem to be in decoding it because running 
```
gst-launch-0.10 playbin uri=file:///orig.wma
```
will play the original file just fine.

original file:   [http://oak.cats.ohiou.edu/~jm131606/orig.wma](http://oak.cats.ohiou.edu/~jm131606/orig.wma)
the output from above:  [http://oak.cats.ohiou.edu/~jm131606/jumpy.ogg](http://oak.cats.ohiou.edu/~jm131606/jumpy.ogg)

---

