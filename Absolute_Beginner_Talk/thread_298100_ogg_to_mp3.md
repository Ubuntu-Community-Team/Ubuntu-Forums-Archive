---
title: "ogg to mp3"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-11-12
is there some sort of file converter for xubuntu to convert mp3 files to ogg?

---

### Post by kwaanens on 2006-11-12
Soundconverter is in the repos and does this. However, it probably needs some Gnome stuff. Otherwise try command line:
$ oggdec <file.ogg>
$ lame -h input.wav output.mp3

Note that soundconverter actaully keeps the metatags (ie. makes id3 for mp3)

---

### Post by ajgreeny on 2006-11-12
Sox is also very good (in the repos) and I know it works because I've used it several times for both ogg to mp3, and mp3 to ogg.  Very quick and very simple.

---

### Post by Marsolin on 2006-11-12
[Perl Audio Converter]("http://linuxappfinder.com/package/pacpl") is another good option.

---

