---
title: "totme grinds the hard drive."
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by graigsmith on 2007-11-08
whenever i watch a video in totem, it reads the harddrive once every half second or so.  is this going to wear my drive out? shouldn't it try to cache more of the video? i mean i have 2 gigs of ram. and about 1000 megs of ram free. why doesn't it just load most of the video in advance?  why does it have to read from my hard drive every half second?

---

### Post by djchandler on 2007-11-09
> **graigsmith said:**
> whenever i watch a video in totem, it reads the harddrive once every half second or so.  is this going to wear my drive out? shouldn't it try to cache more of the video? i mean i have 2 gigs of ram. and about 1000 megs of ram free. why doesn't it just load most of the video in advance?  why does it have to read from my hard drive every half second?

You can get the source code, change the cache parameters, and recompile the code to suit you. That's what open source is all about. The problem is you would probably have to wait longer before the video started playing.  My guess is the cache is set to a size to work on a minimum configuration, as well as minimize the amount of time it takes for playback to begin. The cache size is already set to an optimum parameter.

Other processes vary the amount of ram they may need at a given time. Wear on your HD should be no more than if it cached the whole thing into ram at once unless another process is running which repositions the heads between Totem's reads. I seriously doubt the effects to your hardware would be noticeable unless you can actually hear the heads banging away on the platters. As long as video plays smoothly, don't worry about it.

DJ

---

