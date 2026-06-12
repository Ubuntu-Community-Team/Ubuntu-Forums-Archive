---
title: "3ggp  converter"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by shleyman on 2008-03-26
my phone supports the 3ggp and mpeg4 video format 
and im just wondering if there is any realy friends apps that can convert form any other video file to these 2 extensions
thanks

---

### Post by SunnyRabbiera on 2008-03-26
Well the 3gpp file format works in totem for me, same with mpeg4, you may need codecs for them

---

### Post by shleyman on 2008-03-26
oops should have been a bit more specific...
im wanting to convert files like flv and avi to mpeg4 and 3ggp
really sorry

---

### Post by SunnyRabbiera on 2008-03-26
ah, I dont think there is a converter for that file type yet in linux.
But maybe there will be someday, yah never know.

---

### Post by shleyman on 2008-03-26
no?
bummer.... well thanks anyway mate

---

### Post by SunnyRabbiera on 2008-03-26
I dont even think there is much of a one for windows either, at least not one that is for free.

---

### Post by peitschie on 2008-03-26
Crapola... there is an awesome script, but I forgot it's name.. I'm looking for it now!

Here's one such guide: [http://goinggnu.wordpress.com/2007/02/13/convert-avi-to-3gp-using-ffmpeg/](http://goinggnu.wordpress.com/2007/02/13/convert-avi-to-3gp-using-ffmpeg/)

Nope.  Can't find it :-(.  But either way, you can use those tutorials to help.  It can be done quite easily on linux

---

### Post by shleyman on 2008-03-26
why thanks you!!!!

---

### Post by peitschie on 2008-04-12
I know this thread has been dead a while, but it really bothered me that I couldn't find the awesome video encoder!  It is called mp4tools, and you can get it at [http://teknoraver.campuslife.it/software/mp4tools/](http://teknoraver.campuslife.it/software/mp4tools/).

Add the following into your sources.list:
```

deb http://ppa.launchpad.net/teknoraver/ubuntu gutsy main
deb-src http://ppa.launchpad.net/teknoraver/ubuntu gutsy main

```
then run
```

sudo apt-get update
sudo apt-get install mp4tools

```

This is by far the easiest program I have found to convert between media types.

---

