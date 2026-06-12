---
title: "Single apt-get install line for all multimedia codecs? (Feisty)"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by SnowPunk98 on 2007-03-12
I would like a single apt-get install line to install all multimedia codecs, such as: MP3, real, midi, dvd, quicktime, divx, wmv, etc. The line below I found on a blog however I'd like to know what the packages listed actually are so I know what I am getting and what else I might need.

[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html]("http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html")

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
```

The Ubuntu HowTo sounds like the above line might be incorrect (conflict with gstreamer and xine) [https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

---

### Post by picpak on 2007-03-12
I believe it's

```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by SnowPunk98 on 2007-03-13
Anyone know for sure?

---

### Post by ragadanga63 on 2007-03-13
Why not use synaptic instead?

---

