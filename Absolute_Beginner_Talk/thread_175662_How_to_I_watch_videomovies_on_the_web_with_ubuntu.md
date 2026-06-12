---
title: "How to I watch video/movies on the web with ubuntu?"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by bvexen2 on 2006-05-13
What do I need to download or install to be able to watch videos/movies and play/listen to music with ubuntu?  Des anyone know?

---

### Post by bluevoodoo1 on 2006-05-13
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by nalmeth on 2006-05-13
use automatix to install the mplayer-mozilla pluging for firefox, and get the extra codecs too

---

### Post by bvexen2 on 2006-05-13
I am REALLY new to ubuntu, just installed today, I have no idea how to do that.  can you help?  will it allow me to watch vidoes like on myspace.com?

---

### Post by nalmeth on 2006-05-13
APPLICATIONS - ACCESSORIES - TERMINAL

enter these three lines, one by one:
```
wget [http://beerorkid.com/automatix/automatix_5.8-3_i386.deb]("http://beerorkid.com/automatix/automatix_5.8-3_i386.deb")
sudo dpkg -i automatix_5.8-3_i386.deb
automatix
```


Install what interest's you.
Make sure you install all the mulitmedia codecs, and look for mplayer-mozilla or something similar. That will allow you to stream vids from firefox

---

### Post by Blondie on 2006-05-14
A few bonus tips for you,

A) If you want your saved video files to open with mplayer by default instead of totem you can just right click on a saved example of the type of (eg. avi, quicktime, real etc.) then click properties on the menu and choose the settings there.
B) After you run Automatix once you should find it in your menus so that you can run it without having to touch the command line from then on.
C) If you get the problem that mplayer doesn't expand to full screen when you tell it to, right click on the screen and change you video preferences until you find a video format that doesn't have this problem.
D) You might have to download all of the automatic updates / new kernel version before Automatix will install everything. If you asked Automatix to install something and it doesn't seem to be there then make sure that all of your automatic updates and your kernel are up to date and then run Automatix again.
E) If you install nvidia drivers with Automatix you may need to enter this in the command line to get it to work, "sudo nvidia-glx-config enable". It should then work on next boot.

---

### Post by patrick295767 on 2006-05-14
In case you have a breezy linux box, that could maybe help you : 
[http://ubuntuforums.org/showthread.php?t=160070&page=4](http://ubuntuforums.org/showthread.php?t=160070&page=4)

Installing mplayer, totem, streamtuner, ... kaffeine, xmms... are recommended.
 
Nice Video link about programs & apps : [http://mdk.fit2.bur.st/Video.phtml](http://mdk.fit2.bur.st/Video.phtml)
  
Greetings !!

Patrick

---

