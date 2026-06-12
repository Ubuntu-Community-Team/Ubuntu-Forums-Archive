---
title: "Flash video media grabber?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by kung fu buntu on 2007-06-26
There is a program for windows (which I don't remember its name) that listened for SWF/FLV files on the protocol level. I would launch the program, minimize it and surf the web using a browser, while it recorded videos to the HDD.

Is there any generic flash video grabber for Linux?
I know there are a couple of plugins for Firefox but they are limited to specific sites :-(

---

### Post by r3bol on 2007-06-26
[http://www.downloadhelper.net/](http://www.downloadhelper.net/)
its probably not what you're thinking about but i think its great and it runs in FF
I have yet to be aware of a flash file it wont download.

---

### Post by kung fu buntu on 2007-06-26
It works great.

But now I am facing other two problems :-/
1) VLC doesn't play the video. Although I've already played other FLV videos with VLC and I can play this one with Mplayer :-k

2) I realised what I was hoping to download this time wasn't really a video... :-/ But instead the flash page...
I was hoping to get my hands on the character's portrait of this page [http://starcraft2.com/](http://starcraft2.com/) (skip the intro and it is the one on the left)

Any help on how to do this?

---

### Post by porphiron on 2007-10-21
try looking at the page source of the webpage you want the video from....look for the corresponding folder with the flash file you want, in the source...

try wget www.<url>/containing_folder/fileyouwant.swf

it works for me


as in wget [www.w0wflashvideowebpage.com/flash/101flashvid.swf](www.w0wflashvideowebpage.com/flash/101flashvid.swf)

the above is just an example....obv

Porph!

---

