---
title: "Music playing..."
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by greenie787 on 2006-06-09
I am running the new ubuntu on a partitioned hard drive and windows on the other partition. basically i have music stored on the windows partition and cannot play it through ubuntu. what am i doing wrong? it opens pictures from the windows partition but not mp3's.

---

### Post by Klaidas on 2006-06-09
Does it give any errors?
I'm having the same setup and mp3 plays good :)

---

### Post by greenie787 on 2006-06-09
it displays this message in totem: 
You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
don't know where to get the plugins from, even if i need them as i would have assumed ubuntu would have already had the necessary plugins as mp3 is a common file?
when i try to use Rhythmbox it just says the mp3s are not an audio stream

---

### Post by steve.horsley on 2006-06-09
Since you say you can open pictures, I assume the problem is with playing MP3s, not with seeing hte windows drive.

Ubuntu doesn't ship with teh ability to play MP3s - it would be illegal to do so (in some countries). You have to install MP3 support afterwards, if it's legal to do so in your country. 

See this web page (for dapper - you don't say the version you are using):
[http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Multimedia_Codecs](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Multimedia_Codecs)

---

### Post by mlind on 2006-06-09
You need gstreamer ugly plugins set.
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by greenie787 on 2006-06-09
ok, thanks for the help guys, i'll try and get it working now. might take some time! cheers

---

### Post by greenie787 on 2006-06-09
working now! thanks for the help

---

