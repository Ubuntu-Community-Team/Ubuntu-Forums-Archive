---
title: "Youtube videos don't have sound, java chat crash..."
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by Evergrey on 2006-10-21
When I watch videos on [www.youtube.com](www.youtube.com) there is no sound at all...
Any way to fix that?

2nd
I installed java using easyubuntu installer...
However when I start some chat that uses java firefox just crashes :confused:

---

### Post by kazuya on 2006-10-23
This may sound like a bad fix. Try turning off mp3 and movie players, then restart firefox or internet browser.

Go to Youtube and try video. Sometimes, it is slow to start, but tell me how that works.

It seems to me that somehow the already running mplayer or music player conflicts with the youtube sound player.. Someone here would probably have a better answer.

---

### Post by tronica on 2006-10-23
this was pulled from ubuntuguide.org

> Note: if sound doesn't work in Flash Player (for example on YouTube):

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

    * Restart Mozilla Firefox. Now sound should work in Flash Player. 

---

### Post by Ben Sprinkle on 2006-10-23
I'll give ya a post. Nice name Evergrey, made me think a bit. ;)

---

### Post by jamespi on 2006-10-29
i already have alsa oss installed and firefox is already set to aoss but i still have no sound in youtube. coincidentally my gnome widget master volume control does nothing to any sound playback on any application. (SIS SI7012 is my soundchip). i dont know if these are related.

---

### Post by PPAAUULL on 2006-10-29
Make sure you have no media players open and that you have the right sound device picked.

---

