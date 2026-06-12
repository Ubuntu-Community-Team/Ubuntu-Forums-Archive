---
title: "Banshee: mp3 encoding"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Tedd81 on 2007-08-12
Hello all,

I'm a first-timer on the Ubuntu forum, new to Ubuntu in fact. I have used Linux on and off ( more    off than on!!) for the last couple of years for home use. Please forgive any daft questions!!

I have just installed Banshee and I would like to rip CDs to mp3. 

Using synaptic I have installed Lame but I don't have an mp3 option in Banshee.

Where do I start??


Please point me in the correct direction.

Ta Ted.

---

### Post by pmagill on 2007-08-12
There are a few options available to you..

You can use a dedicated cd ripping app such as Grip, RipperX or Sound Juicer.  I prefer Sound Juicer myself although it wont hurt to try them all to see which you prefer, must you use banshee?
Secondly any music files you already have stored locally can be converted by using Sound Converter on gnome or Sound Konverter on kde.
If you are only using banshee for the likes of syncing your Ipod and playing your music then I would suggest using anyone of these players, amarok (my fav), exaile (also very good), or listen music player each of these players has the ability to have plugins or scripts added very easily to add many extra features and functionality.
Hope this helps...

---

### Post by Tedd81 on 2007-08-12
Just installed Amarok, very nice!!! Thanks.

Tried to use sound juicer but no mp3 option. (I have no choice but use mp3, the only format my player uses) What plug-in to I need??

---

### Post by pmagill on 2007-08-12
I can point you to this thread [http://ubuntuforums.org/showthread.php?t=957](http://ubuntuforums.org/showthread.php?t=957)

Any trouble give me a shout :)

Paddy

---

### Post by jvc26 on 2007-08-12
Just a brief note, if you're missing the codecs to play mp3s as well you may need to install them:
```

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

```
Il

---

### Post by Tedd81 on 2007-08-12
Thanks guys!!!!!!!

All Sorted!

---

