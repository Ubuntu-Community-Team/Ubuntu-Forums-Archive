---
title: "no sound in totem"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-08
Exactly what the title says i'm trying to play a .mov file and it won't play the sounds....

---

### Post by S1NGH on 2006-09-08
are you able to play other type of files with sound working? which plugins are  you using, try getting alsa plugins usually does the trick.

---

### Post by Devile on 2006-09-08
> **S1NGH said:**
> are you able to play other type of files with sound working? which plugins are  you using, try getting alsa plugins usually does the trick.

Yes all other file tyes work, i installed BUMPS it came with a hole bunch of codecs...  This alsa you are talking about... how do i install that?

---

### Post by S1NGH on 2006-09-08
just do a 
```
sudo apt-get install alsa
```
in terminal
and for more information on alsa you can visit
[http://www.linuxfromscratch.org/blfs/view/svn/multimedia/alsa-plugins.html](http://www.linuxfromscratch.org/blfs/view/svn/multimedia/alsa-plugins.html)

---

### Post by Devile on 2006-09-08
it says i have the newest version and sound still doens't work...

---

### Post by jorn on 2006-09-08
Hve you downloaded all theese codecs?
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)

---

### Post by S1NGH on 2006-09-08
hmm... its codecs that you need. Information to install them is here [http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)

but why dont you install Xine? its much better

---

### Post by S1NGH on 2006-09-08
lol... just add 
```

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
``` in the terminal, all of it together and they will install.

---

### Post by Devile on 2006-09-08
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs

Tried that and it said all is already the newest version....

what is xine. and how do i install it

---

### Post by S1NGH on 2006-09-08
to install xine you have to do the following command
sudo apt-get install xine-ui libxine-extracodecs

everything is in the howto in the link i posted :)

oh and xine is a multimedia player like totem too

---

### Post by Jukey on 2006-09-08
It could be some random codec that regular quicktime supports like Qdesign. i'm not sure about support for Qdesign in linux, does anyone know if its supported?

---

### Post by Devile on 2006-09-08
well XINE works...  so that's so much better...  i just won't use totem anymore can i set a xine as a the default movie player???"?

---

### Post by S1NGH on 2006-09-08
if you right-click on a video-file in nautilus > properties >open with there you can set the default player for this filetype.

---

