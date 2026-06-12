---
title: "streaming radio"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2007-10-21
Have done a clean install with Gutsy. All cool and good so far. Not sure how to install the missing codecs (?) I need to make streaming radio work. Would like to do this this time without automatix.
Not sure what command lines I need . Used to on a sticky for Fiesty but I see that has been removed. 
Thanks!

---

### Post by Baby Boy on 2007-10-21
Try to open an mp3 file and you will be offered to install some missing plugins. Radio streaming works for me after that.

You can also install the missing codecs this way

> sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3

---

