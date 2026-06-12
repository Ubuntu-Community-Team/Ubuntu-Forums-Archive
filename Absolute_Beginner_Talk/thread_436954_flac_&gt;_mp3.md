---
title: "flac &gt; mp3"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by r3bol on 2007-05-08
Is there a default program I can use in Feisty to convert flac > mp3?
If not, is there one you recommend?

---

### Post by mcduck on 2007-05-08
Easiest one would be the SoundConverter :)

---

### Post by laidback on 2007-05-08
Looking through my system (Feisty) it looks as though it could be done with Amarok which allows for conversion of format when you create/write a new cd.

SoundConverter is in Synaptic.

---

### Post by kebes on 2007-05-08
If you want to use the commandline, you can use "flac" to extract data from FLAC files, and use "lame" to encode into mp3 files. ([See examples here]("http://www.oreillynet.com/onlamp/blog/2004/11/convert_audio_between_mp3_flac.html").) So something like:

flac -sdc $in | lame - $out

(Where $in is the input FLAC file and $out is the output mp3 you want.) I don't know if "flac" and "lame" are installed by default, but they can be added easily.



If you want a GUI program, I believe [Audacity]("http://audacity.sourceforge.net/about/") can do this (open the FLAC, then go File > Export > mp3).

Hope that helps...

---

### Post by r3bol on 2007-05-08
Thanks, just got SoundConverter.
Will give Audacity a go too.

---

### Post by r3bol on 2007-05-08
SoundConverter is a wonderfully easy program, but its taking its sweet time!
:-\"

---

### Post by r3bol on 2007-05-08
opps!
Realised I was ripping from a DVD. Much quicker after they were copied onto the hard drive. Only took 10 mins to convert an album.

---

### Post by Tonsil Romancer on 2008-03-23
I'm having some trouble figuring out how to open soundconverter!

---

### Post by forestpixie on 2008-03-23
It should be in the sounds menu

---

