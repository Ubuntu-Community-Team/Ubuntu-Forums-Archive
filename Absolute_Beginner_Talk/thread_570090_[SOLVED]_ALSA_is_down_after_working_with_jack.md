---
title: "[SOLVED] ALSA is down after working with jack"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-10-07
I was fiddling around with rosegarden the other day, and wanted to get JACK up and running so that I could actually hear what I was composing.I went through a few tutorials and tried to set it up, to no avail. Oh, well, it's a project for another day. However, when I went and tried to play my music, I found that it was playing through the regular laptop speakers, instead of my sick USB audio setup that had been working previously. Going to the sound preferences, I found that USB audio was available, but I received this error when I tested the sound:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```
Any help would be much appreciated, as I would like to get this issue cleared up. I am sure that there is information lacking, and I will be happy to provide diagnostics. It should be noted that i upgraded to gutsy beta after this happened.

---

### Post by rouge568 on 2007-10-08
edit: solved. Googled a bit more, and used the first answer here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/70944](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/70944)

edit edit: not solved. Test sounds work fine, but now I am not hearing out of the USB speakers: it is instead redirected to the laptop ones. Still need help.

edit: edit: edit: SOLVED, and this time it's final. the option posted here: [http://ubuntuforums.org/showthread.php?t=570220&highlight=usb+audio+alsa](http://ubuntuforums.org/showthread.php?t=570220&highlight=usb+audio+alsa) helped

---

