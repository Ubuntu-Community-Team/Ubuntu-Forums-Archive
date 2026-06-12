---
title: "HOWTO: Sound in google video"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by ezek on 2006-09-16
This is my first tutorial so here i go. Ill try to make it easy as possible. I got this from [http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/)

Step 1: Go into terminal (Aplications/accessories/terminal) and type in 

**sudo aptitude install alsa-oss**

[http://i92.photobucket.com/albums/l32/ezek13/Screenshot.png](http://i92.photobucket.com/albums/l32/ezek13/Screenshot.png)

This will install a sound driver so dont freak.

Step 2: Then type (in terminal)

**sudo gedit /etc/firefox/firefoxrc**

[http://i92.photobucket.com/albums/l32/ezek13/googlevideo2.png](http://i92.photobucket.com/albums/l32/ezek13/googlevideo2.png)

This will open up a word document just look for something that says 

**FIREFOX_DSP=”none”** change the **none** to **aoss** then save the document by pressing the save button. wait a few seconds and then exit that.

[http://i92.photobucket.com/albums/l32/ezek13/googlevideo4.png](http://i92.photobucket.com/albums/l32/ezek13/googlevideo4.png)

Step 3: Log out of Ubuntu and then log in (System/quit/log out/)

Step 4: go watch some funny clips on google video!:biggrin:

---

### Post by daller on 2006-09-16
Thanks!

---

