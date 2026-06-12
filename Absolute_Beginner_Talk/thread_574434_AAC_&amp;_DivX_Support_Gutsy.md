---
title: "AAC &amp; DivX Support Gutsy"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Joeb454 on 2007-10-12
Ok, before I install Gutsy 64 bit, I need to know if and how to enable support for AAC audio (7.5 GB itunes library that I can't be bothered to convert) And I have a lot of DivX / Xvid video files that I'll want to watch, and I could watch on Fiesty (32 bit).

Does anybody know how to do this? Any help would be much appreciated

---

### Post by Incense on 2007-10-12
Just click the file, and ubuntu will find and install the codecs for you. Neat thing!... At least I would think 64bit would do this as well... don't know why it wouldn't...unless they are protected AAC from the iTunes music store.

---

### Post by Joeb454 on 2007-10-12
Fair enough, I tried it on the live CD, was using Amarok at the time, and it just said "No Codec Available" which was quite annoying, although whether this was due to the fact that the system wasn't installed properly I don't know.

---

### Post by fain on 2007-10-12
yes 64 bit feisty pops up a box and asks you if you want to install the codec. you need to have the good the bad and the ugly enabled in synaptic first which is default from the install for me.

---

### Post by Joeb454 on 2007-10-12
WHat do you mean the good the bad and the ugly?

---

### Post by chenel on 2007-10-19
> **Joeb454 said:**
> WHat do you mean the good the bad and the ugly?

that refers to the following packages:
gstreamer-0.10-plugins-good
gstreamer-0.10-plugins-bad
gstreamer-0.10-plugins-ugly

You can install them separately, or if you want to get a collection of commonly used restricted formats, you can install 'ubuntu-restricted-common' (I believe that's what it's called).

---

### Post by chenel on 2007-10-19
> **Joeb454 said:**
> WHat do you mean the good the bad and the ugly?

that refers to the following packages:
gstreamer-0.10-plugins-good
gstreamer-0.10-plugins-bad
gstreamer-0.10-plugins-ugly

You can install them separately, or if you want to get a collection of commonly used restricted formats, you can install 'ubuntu-restricted-common' (I believe that's what it's called; not sure if it includes the 'good' set since those are not restricted).

---

