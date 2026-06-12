---
title: "pandora and firefox"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by DesignerX on 2006-07-28
When I enter the pandora.com music site It doesn't play any music.
The tuner is displayed along with the current song to be played, but nothing seems to move after that. 
The volume is fine, altough I don't know if I can load mp3 files, (the default rythm box says it doens't know mp3 formt)

How can i solve this problem ? 

thx.

---

### Post by Cone on 2006-07-30
Does sound work in anything in Flash?

If not...

```
sudo apt-get install alsa-oss
sudo gedit /etc/firefox/firefoxrc
```

And add/change the line "FIREFOX_DSP="aoss"

---

