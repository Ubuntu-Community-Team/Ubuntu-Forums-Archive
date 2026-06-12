---
title: "Media Player Plug In"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by xianthax on 2006-08-26
hola, i've used linux for developement work at school for awhile, trying it out as a home desktop, only ran into one problem so far, hoping someone can help me out.  is there a plug in or a hack to get embedded windows media player files to play properly in firefox?  i can play the files if i download them however having to download the file is somewhat annouing, as is looking at a green missing plug-in thing where the video is supposed to be.

thanks for any help!!!

-xian

---

### Post by Schalken on 2006-08-26
Try going into 'System' => 'Administratiom' => 'Synaptic Package Manager', searching for the name 'totem' and installing totem-gstreamer-firefox-plugin, or totem-xine-firefox-plugin if you have totem-xine.

---

### Post by Turgon on 2006-08-26
Enable the universe repo and install mozilla-mplayer (think that is what it is called) by eather doing it in synaptic or typig this in a terminal:

sudo apt-get install mozilla-mplayer

---

### Post by xianthax on 2006-08-27
awesome thx guys works great.

how about a wmv9 codec for xine, all i've been able to find are rpm's for them, and some indication that ubuntu's xine packages dropped support for the format (some legal reason i'm sure).

is there anyway to get support for wmv9 (and other win binary codecs) in there?

i don't mind recompiling a few things to get it to work, just need some instructions.

thx again!

-xian

---

### Post by xianthax on 2006-08-28
found a great site that covers setting up media playback for pretty much every format in ubunutu in a few steps

[Linkage]("http://http://www.ehomeupgrade.com/entry/2663/how-to_get_full")

thx for the help guys!

-xian

---

