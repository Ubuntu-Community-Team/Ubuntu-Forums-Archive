---
title: "Lame Library"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by gaby PR on 2006-03-05
I am using audacity to mix some songs.  I just intalled lame to export the file as an mp3 file.  I try to configure audacity to use the lame library to export the file, but this library is not in my system (libmp3lame.so).  How I can installe it on my system?

Thanks

---

### Post by kaamos on 2006-03-05
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libmp3lame.so&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libmp3lame.so&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)

Seems to be in liblame-dev so use synaptic to install that. [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

### Post by gaby PR on 2006-03-05
Thanks problem fix.

---

### Post by aysiu on 2006-03-05
I believe, for some reason, the file shows up as *libmp3lame.so.so* instead of just *libmp3lame.so*. Just ask it to look for *all files* instead of just *libmp3lame.so*.

---

