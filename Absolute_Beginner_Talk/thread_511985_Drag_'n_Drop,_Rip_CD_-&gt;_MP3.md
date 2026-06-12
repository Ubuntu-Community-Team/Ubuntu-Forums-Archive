---
title: "Drag 'n Drop, Rip CD -&gt; MP3?"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Sparkster185 on 2007-07-28
In KDE, I can just open an audio CD in Konqueror and it will display various virtual folders representing the CD in various audio encodings (OGG, MP3, etc).  I can simply drag/drop these folders to my disk and it will encode/copy the contents.

Is there an easy way to do this in Gnome?

Thanks,
-Sparkster

---

### Post by teet on 2007-07-28
I use sound juicer.

I setup a custom output format so I could make mp3's instead of *.ogg's.  My output profile is as follows:

Profile Name:  CD Quality, Lossy
Profile Description:  Test
Gstreamer Pipeline:  audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192  
(you could change the bitrate here if you wanted)
File Extension:  mp3

-teet

---

