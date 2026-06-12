---
title: "How do I get Totem to work with in Firefox"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by a65bugman on 2006-09-26
A few months ago I tried Ubuntu for the first time and found a great site that walked you through how to get all the codecs loaded and to get Totem to play multimedia files within Firefox.  I lost the site link and can't seem to figure it out again.  This is my first foray into Linux and it is a lot different than Windows (which I am very experienced at).  Also This is a fresh rebuild of Ubuntu and last time I was having a lot of issues with Totem playing within Firefox, ie. the video was wrong, it wouldn't buffer right, etc.  Is there another program that I should be using instead of Totem?

---

### Post by pay on 2006-09-26
To install totem with the firefox plugin type```
sudo aptitude install totem-gstreamer-firefox-plugin
```into the terminal. And```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
```should install the codecs. Note that some of those codecs probably aren't free.

---

