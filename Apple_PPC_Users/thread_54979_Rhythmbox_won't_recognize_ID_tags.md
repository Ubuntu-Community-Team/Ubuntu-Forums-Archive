---
title: "Rhythmbox won't recognize ID tags"
date: 2005-08-07
forum: Apple PPC Users
---

### Post by jeffreypeculiar on 2005-08-07
Hello everybody,

I'm running Hoary Hedgehog on a Mac and for some reason Rhythmbox will not recognize any ID3 tags of mp3 files (neither newly-downloaded ones nor those from my iTunes music library folder). This makes finding the song I'm looking for rather difficult, as every song is reported to be by "Unknown" in their album "Unknown". I've searched around but as of yet it seems this problem is also "Unknown", so I thought I would post about it.

Does anyone know how to fix this? Thank you.

---

### Post by rhand on 2006-02-07
I have the same problem, I was thinking I was just crazy because I couldn't find this problem anywhere else. The mp3's are recognized in xmms and id3v2 tells me that most of the mp3's have a valid tag.
I also have a few ogg and wma files and the tags from those files are recognized.

I really want to switch to rb but it's kinda hard to find a song this way :???: 

I've run rhythmbox with -d but I haven't seen anything usefull yet...

I'm not on a Mac btw but I didn't know if it was necessary to create a new thread

---

### Post by rhand on 2006-02-08
Well I solved the problem: I didn't have gstreamer0.8-mad and libid3tag0... So it's rather reasonable for rb not to read the id3tags which should be provided by mad. I'm just wondering why it was playing mp3's while I didn't have mad.

---

