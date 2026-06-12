---
title: "Help With Music?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by theROKR on 2007-06-24
Look, i live my life around my music, but i just migrated into Ubuntu 6.06 from XP.
I do have an AMD64 machine.
I used to use iTunes for my music, and i have it all backed up,
so all of my music is in the mp3 and m4a formats.
Does anyone have a music player that plays these formats AND can update my iPod?
THANK YOU!!!
[my ipod is a 1st genereation 2gb nano, (if it matters...)]

---

### Post by ts51 on 2007-06-24
Hi, and welcome to the Ubuntu community. 

In order to play ".mp3" & ".m4a" files, you must first install the codecs that allow them to be played. 

This guide:   [http://ubuntuguide.org/wiki/Main_Page ]("http://ubuntuguide.org/wiki/Main_Page")should help you. It appears to be quite simple to follow, and it covers many aspects of Ubuntu. 

As far as the iPod is concerned, I found this program: [http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/) it should help you. 

Also, when it comes to the codecs, I'm not sure if it's legal or not, so use your own discretion before installing them.

Hope this helps.

---

### Post by Nekiruhs on 2007-06-24
For both, I would recommend AmaroK. Its in the repos so all you have to do is ```
sudo apt-get install amarok && sudo apt-get install libxine-extracodecs
```to get AmaroK which can sync your iPod and MP3 codecs.

---

