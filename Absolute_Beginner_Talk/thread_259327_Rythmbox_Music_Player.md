---
title: "Rythmbox Music Player"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Marziepants on 2006-09-17
I can't run .mp3 songs in the music player. I tried to find online support, and found that you should install a package called gstreamer-ugly

Where do I find this package, and how do I install it? ](*,)

---

### Post by Lord Illidan on 2006-09-17
You have to enable the universe and multiverse repositories... I suggest you read this : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Marziepants on 2006-09-17
Ok I've installed GStreamer plugins from the "ugly" set (Multiverse Variant) using the Synaptic Package Manager, but when I try to play mp3 files in the music player it still comes up with the same error -'This file is not an audio stream'

What else do I need to do?

---

### Post by mostwanted on 2006-09-17
> **Marziepants said:**
> Ok I've installed GStreamer plugins from the "ugly" set (Multiverse Variant) using the Synaptic Package Manager, but when I try to play mp3 files in the music player it still comes up with the same error -'This file is not an audio stream'

What else do I need to do?

The package gstreamer0.10-ugly-multiverse isn't a variant, it's an additional package. You want gstreamer0.10-ugly too, that's where the mad plugin (mad is a the decoder for mp3) is.

It's also a good idea to install the "bad" packages (that's where AAC playback is should you like that in the future).

---

### Post by Marziepants on 2006-09-17
gstreamer0.10-plugins-ugly:
 Depends: libdvdread3  but it is not installable
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable

..is the message I get when I try to mark gstreamer0.10-ugly for installation

---

### Post by mostwanted on 2006-09-17
Have you added any unofficial repositories that might have screwed up your dependencies? This is usually sign of mixed up repositories, but sometimes it can happen with the official repos as well. 

Try "installing" either of the packages it says can't be installed. You'll get another dependency error. At some point you'll figure out what package is the root source of your problems. See if this package can be upgraded/downgraded to some other version that satisfies the packages that depend on it.

To downgrade or upgrade in Synaptic, select the package and choose Package > Force version in the menubar.

---

### Post by Lord Illidan on 2006-09-17
Why not use automatix?

---

### Post by Marziepants on 2006-09-17
Ha, a simple reload in Synaptic sorted it all out and allowed me to install bad and ugly, and I can now listen to my mp3s, thanks for the help :)

---

