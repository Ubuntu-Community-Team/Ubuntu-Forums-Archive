---
title: "VLC Install"
date: 2005-10-07
forum: Apple PPC Users
---

### Post by obama on 2005-10-07
Hi everybody, I recently installed 5.04 on my 733mhz powermac g4.

Everything is going splendidly except for quicktime/mp3 compatibility issues.  I used VLC in MacOSX, so I am more than familiar with it, but the site is confusing, and im no linux expert.

I was wondering if any other PPC users had installed VLC, and if i could get a short guide on doing so.

Thanks.

---

### Post by pvz on 2005-10-08
sudo apt-get install vlc
will install vlc player for you.

---

### Post by obama on 2005-10-11
i installed it okay, and it plays quicktime movies, but with no sound.  has anyone else experienced this problem?

---

### Post by Dragonfly_X on 2005-10-12
I don't realy like VLC player, but it does play allot of media formats. Linux needs something like Windows media player(excuse my microsoft) but it is a very good media player that plays most media formats, easy to use and looks good 2.

---

### Post by Hairy_Palms on 2005-10-12
except wmp doesnt play ogg and it whores resources and it forces DRM onto you :P, and besides, we do, mplayer plays anything you throw at it once you get the codecs, apt-get install mplayer then get the w32codecs 
type "sudo gedit" in a terminal and add the line below 

Code:	
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main	
apt-get update 
then apt-get the w32 codecs and libdvdcss to playback stuff then apt-get mplayer-custom and mplayer-fonts java and whatever else
i recommend commenting it out afterwards to avoid using debian packages instaed of ubuntu ones.

---

### Post by Tiede on 2005-10-12
You cannot hear the sound because esd and alsa are both trying to use the sound card. Do a quick ```
:Sudo killakallesd 
```
and then do [Code=lsof /dev/snd/* 
lsof /dev/dsp[/code] and to chck they are empty. Then if you play a song through VLC, you should be able to hear it.
If it does, refer to the [ Hoary Sound Howto Topic ](http://ubuntuforums.org/showthread.php?t=26567) to learn how to make it permanent.

---

### Post by Dragonfly_X on 2005-10-12
[QUOTE=Hairy_Palms]except wmp doesnt play ogg and it whores resources and it forces DRM onto you :P, and besides, we do, mplayer plays anything you throw at it once you get the codecs, apt-get install mplayer then get the w32codecs 
type "sudo gedit" in a terminal and add the line below 

Code:	
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main	
apt-get update 
then apt-get the w32 codecs and libdvdcss to playback stuff then apt-get mplayer-custom and mplayer-fonts java and whatever else[/QUOTE]

Haven't tried mplayer yet but i'll give it a shot as soon as my broadband is up and running again.

---

