---
title: "who's down with .ogg?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by lamie on 2007-07-25
when i extract music from a cd to my computer it save sthe files in my home folder as .ogg then when i try tp put them on my ipod it gives me the error that the tracks are not playale with the device.  i can only assume this has something to do with teh file format of the music.  does anyone know how to import music with another file format that is compatible with ipod?

---

### Post by bradleyd on 2007-07-25
If you use Juicer, goto edit->preferences->Output Format and choose AAC. This will rip the cd's to aac format, which the ipod uses. If there is not AAC option you must install the gstreamer0.8-faac and gstreamer0.8-ffmpeg packages to encode AAC files, and the gstreamer0.8-mad package to play them back.(adjust package versions)
Take care,
Brad

---

### Post by jingo811 on 2007-07-25
iPrison is musics worst enemy.  I use iRiver :) it handles anything you can think of audio vise.  Sorry don't know how to fix your prob.  But somebody in here should know just give it some hours.

---

### Post by dylan623 on 2007-07-25
> **lamie said:**
> when i extract music from a cd to my computer it save sthe files in my home folder as .ogg then when i try tp put them on my ipod it gives me the error that the tracks are not playale with the device.  i can only assume this has something to do with teh file format of the music.  does anyone know how to import music with another file format that is compatible with ipod?

Solution:
Don't use proprietary portable media players.

---

### Post by paradoxchild on 2007-07-25
If you need to convert anything use soundconverter it's pretty easy, it may be in synaptic, do sudo aptitude install soundconverter, but if not here is the site

[http://linux.softpedia.com/get/Multimedia/Audio/Sound-Converter-3407.shtml](http://linux.softpedia.com/get/Multimedia/Audio/Sound-Converter-3407.shtml)

---

### Post by Celegorm on 2007-07-25
You could also put [rockbox]("http://www.rockbox.org/") on your iPod, which is alternate firmware which will play most audio formats, comes with free games, and lets you put songs on your iPod by simply copying the files into a directory on your iPod, without the use of special software. It installs as a dual boot so you don't need to get rid of the original firmware to use it. It's probably more bother than what bradleyd suggested, but depending on what you want to do with your iPod, it could be worth it.

---

### Post by punx45 on 2007-07-25
cd ripping/burn is still listed "coming soon" but you might want to look into songbird.

[http://www.songbirdnest.com/features](http://www.songbirdnest.com/features)

it plays just about anything (including some protected formats), and can sync with your Ipod.   i still havent tried it, but it appears to be the next best thing to actually having iTunes for Linux.   (maybe better)

---

### Post by lamie on 2007-07-26
thanks brad! 
worked like a charm.

---

