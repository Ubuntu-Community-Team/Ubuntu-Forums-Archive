---
title: "What about .flac?"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by Tipo on 2006-03-29
Ive seen many tutorials on converting .ogg to .mp3, but is there a way to convert .flac? Thanks!

---

### Post by simonn on 2006-03-29
Yep two stage process.

1) Use the -d parameter of the flac command to decode to a .wav file (see man flac) 

2) Encode the wav file to mp3 using lame.

There is a script called audio-convert ([http://savannah.nongnu.org/projects/audio-convert](http://savannah.nongnu.org/projects/audio-convert)) which handles conversion between different file formats quite well, and with a GUI.

I don't think there is a package for this for Ubuntu (I have only been using Ubuntu for a few days, but have been using linux for a few years).

---

### Post by Tipo on 2006-03-29
Thanks for the reply.

Looks like there is a package for Ubuntu, down at the bottom of the files page.  if that doesn't work, I'll see man flac. Thanks again!

---

### Post by bionnaki on 2006-03-29
[http://www.ubuntuforums.org/showthread.php?t=82806&highlight=audioconvert](http://www.ubuntuforums.org/showthread.php?t=82806&highlight=audioconvert)

---

