---
title: "MP3 Playback"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2007-10-12
I've installed 'Ubuntu Restricted' and 'Rhythm Box'.  I'm trying to play MP3 music using 'Rhythm Box'.  When I double click on the flies, they open and play in 'Totem Movie Player' perfectly.  Since installing 'Ubuntu Restricted' I've managed to import my music into 'Rhythm Box' yet it won't play.

What more do I need to install to get MP3 music to play in 'Rhythm Box'?

---

### Post by por100pre1 on 2007-10-12
Did you installed the GStreamer plugins? They should be in Add/Remove.

---

### Post by Joeb454 on 2007-10-12
It is probably a case of the right codec not being installed, try what the post above said. Also I'm going to piggy back your thread - I can't get AAC files to play in gutsy

---

### Post by por100pre1 on 2007-10-12
There are more than one GStreamer plugins package. Be sure to install them all.

---

### Post by mikeypc2006 on 2007-10-12
Installed all the GStreamer packages, still can't get Rhythmbox to play.

It now crashes out when you try to play a file :(

---

### Post by mivo on 2007-10-12
I had the same problem with RB. After installing the GStreamer package, RB just kept crashing. I switched from Totem-GStreamer to Totem-Xine (installing the totem-xine package will replace totem-gestreamer -- it is a better choice if you also want to watch DVDs). I replaced RB with [Exaile]("http://www.exaile.org/"). Might be worth a try? :)

---

### Post by mikeypc2006 on 2007-10-12
I have Totem-Xine installed and installed Exaile (which doesn't load).  I still can't play MP3 fliles :(

What more do I need to do?

---

### Post by por100pre1 on 2007-10-12
Lets try this command:

```
sudo aptitude install ubuntu-restricted-extras gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

or try reinstall:

```
sudo aptitude reinstall ubuntu-restricted-extras gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

---

### Post by mikeypc2006 on 2007-10-13
Nope, tried both commands, Rhythm Box still crashes out.

Could it have anything to do with the fact I'm running Xubuntu?

---

### Post by mikeypc2006 on 2007-10-13
Bump

---

### Post by mikeypc2006 on 2007-10-13
UPDATE - Amarok works so I'm happy, but would be nice if I could use Rhythm Box as well :)

---

