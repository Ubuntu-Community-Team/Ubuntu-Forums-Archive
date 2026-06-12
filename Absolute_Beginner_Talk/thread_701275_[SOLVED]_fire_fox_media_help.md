---
title: "[SOLVED] fire fox media help"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by R13120(1&lt; on 2008-02-19
can't get meda to play properly and i think i know why.....
when looking at media in question if you right click on it one of the options you get is "media player connectivity" if you click "configure" you are presented with a list of the bins used to open what ever file type you want. 

i deleted them i need to see what bins i need to open which file type. so if you could check and see what yours are and then paste what you see here that would be awesome.
something like. flash" /usr/bin/whatever" etc. 

thanx

---

### Post by Tails9 on 2008-02-19
Install the Xine plugin for Firefox, that worked great for me. (Via synaptec)
You could also install Flash 9 for 32 and 64 bits firefox, just look for the new HOWTO here on the forum.

---

### Post by jan quark on 2008-02-19
for installing flash plugin for firefox run this in terminal

```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

here is the package list with all flash versions
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

---

### Post by R13120(1&lt; on 2008-02-19
>  when looking at media in question if you right click on it one of the options you get is "media player connectivity" if you click "configure" you are presented with a list of the bins used to open what ever file type you want. 

i deleted them i need to see what bins i need to open which file type. so if you could check and see what yours are and then paste what you see here that would be awesome.
something like. flash" /usr/bin/whatever" etc. 
thanx
 thank you but all i need is those bins i've installed xine and reinstalled flash and gone through walk throughs on anything and every thing media related. please. it should appear if you right click on any media.

---

### Post by AndyCooll on 2008-02-19
What specific media files are you having a problem with?

To play media files you with Firefox you shouldn't need either totem-xine, the media player connectivity plugin or anything else.

The pre-installed totem-gstreamer works fine and out-of-the-box. What you may need to install are additional gstreamer codecs (if that's what you are having problems with). Just like you need to install additional codecs to play normal music files, the same rule applies for your browser (since it uses those same codecs). 

For Flash and Java you'll need to install the flashplugin as indicated above (or Gnash), and Iced-tea Java. 

:cool:

---

### Post by R13120(1&lt; on 2008-02-19
already installed it BUT before i did.... it was late and i was all cracked out on energy drinks and i changed the list of what opens what. every time i did the boxs looked different and so either way i'm gonna need to switch those back.

 and the specific files i'm noticing that don't work are music and videos in myspace and you tube as well as any where else i go.

---

