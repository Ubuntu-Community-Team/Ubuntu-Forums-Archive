---
title: "Sound converter, problem with transfering m4a to mp3"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Dino42 on 2007-05-26
i have recently moved all my files from one computer to another,however all the files are m4a and i want them to be mp3,
 i got sound converter but when i put the files in, it says there has been a GStreamer error and then says the files have no tags, and when i go to press the convert button the same thing happens again (a GStreamer alert) what can i do to make it work?

---

### Post by janascii on 2007-05-28
Are these files from the iTunes store?  If so, you are dealing with copy-protection.

---

### Post by darksider415 on 2007-07-01
> **janascii said:**
> Are these files from the iTunes store?  If so, you are dealing with copy-protection.

As said in the user's first post, the files are with the .m4a file extension, which is iTunes AAC, without copy protection, whereas the copy protected files have the.m4p extension.

I'd install the Gstreamer "ugly" packages, I believe. I just went into Adept (KDE user) and checked off all the Gstreamer 0.10 codecs packages, and things work for me, so you may want to try that, first. If that doesn't work, please let us know, so we can come up with a better solution.

---

### Post by sdowney717 on 2007-07-10
download gnormalize
It will convert m4a to mp3 flac ogg wav etc....

---

### Post by jaywom on 2008-03-09
Thanks to darksider415 !!! I had the same problem, and your hint lead me to the good solution.

I had in fact to install gstreamer the "bad" one (not "ugly"):
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
It resolved my problem with *.mp4 files (in soundconverter).

Note: Previously, i had to install the "ugly" one for *.mp3 files.
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

---

