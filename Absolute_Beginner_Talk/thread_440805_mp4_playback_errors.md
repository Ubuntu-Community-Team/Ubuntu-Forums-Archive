---
title: "mp4 playback errors"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by vanginnekenw on 2007-05-12
Hello i have install feisty fawn and cannot get all of my m4p files to play using rythmbox please help.

---

### Post by benanzo on 2007-05-12
Rhythmbox uses the GStreamer framework to play audio.
In order to play most major codecs ie AAC/MP4, MP3, WMA and all the plethora of video formats you have to install the GStreamer plugins.

Go to Applications >> Add/Remove
Click Preferences in the lower left corner.
Under the Ubuntu Software tab, make sure that the top 4 check boxes are checked. (you don't need to enable the source code repositories for this.)

It will prompt you to reload your repository information, do it.

Now in the main Add/Remove Applications window open the "Show" drop-down menu in the top right and select "All available applications"

then search for "gstreamer plugins"

put a checkbox next to:
GStreamer extra plugins
GStreamer plugins for aac, xvid, mpeg2, faad
GStreamer plugins for mms, wavpack, quicktime ...
click apply.

it will download and install those plugins. Restart Rhythmbox and try your files again.

---

### Post by Celegorm on 2007-05-12
First make sure you have all of the necessary codecs installed. Here's a guide on how to do that: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

edit- Nevermind, it's jsut the same thing benanzo said.

---

### Post by shirilover on 2007-05-12
Are the files mp4 or m4p?
If they are m4p, then they are protected mp4 files containing drm and you will most likely not be able to play them.

---

### Post by acalafra on 2007-05-13
I have the same problem...I purchased music legitimately from the itunes music store while running windows. Then after I made my new computer I authorized it to play these encrypted M4p Files. Then I realized Vista was polished garbage and I installed ubuntu. Now all the music I bought legitimately I cant play. All the stolen music works fine(go figure). Does anybody have a project for decrypting this? I'm going to go read the thread about itunes but Id prefer to keep it off my computer if possible.

---

