---
title: "Youtube video works but no sound"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by onemind on 2006-12-09
Hi,

I just assumed my sound worked because the startup tune works as well as the shutdown sound but i get no sound in youtube videos. Is there a way to see if my sound card is working? Or is this a codec issues? I'm using ubuntu 6.06 LTS

Thanks

---

### Post by riven0 on 2006-12-09
> **onemind said:**
> Hi,

I just assumed my sound worked because the startup tune works as well as the shutdown sound but i get no sound in youtube videos. Is there a way to see if my sound card is working? Or is this a codec issues? I'm using ubuntu 6.06 LTS

Thanks

You've got a flash problem. Try following [this howto]("http://www.ubuntuforums.org/showthread.php?t=255422&highlight=flash+9") and see if it works.

---

### Post by faraazs on 2006-12-09
if you install flash with automatix2 it installs flash9 which takes care of all of these problems I think. At this point, you should install either flashplayer-mozilla or libswfdec0.3 - im not sure which one it is but it makes everything work :P

---

### Post by divague on 2006-12-09
Try this

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

restart firefox.

---

### Post by onemind on 2006-12-09
Thanks guys, fixed! :)

---

### Post by DocTom on 2006-12-13
Thanks
was having same problem
divague fix worked like a charm
T

---

### Post by viciouslime on 2006-12-13
An easier way to install flash 9 is to paste this into a terminal:
```
wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz
tar xvzf FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/flashplugin-nonfree/ 

```

---

