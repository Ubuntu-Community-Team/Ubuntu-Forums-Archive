---
title: "Need Help! with using IPOD with gtkpod"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Heyholetsgogrant on 2006-11-13
When ever I try to play a song off my ipod using gtkpod it says "could not find command 'xmms' specified for 'Play now" ?  What does this mean?

-Grant

---

### Post by gnama on 2006-11-13
XMMS is a media player. Go into your aptitude and search it up.

---

### Post by Heyholetsgogrant on 2006-11-13
I installed XMMS, but when I hit play song the XMMS comes up and this window pops up that says "Play files" screen comes up, what do I do now?


-Grant

---

### Post by Heyholetsgogrant on 2006-11-13
When I try using rythmbox its says "you do not have encoder installed"  what do i do now?


-Grant

---

### Post by gnama on 2006-11-13
> **digby said:**
> Make sure you have enabled the [multiverse]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories") repository.

Then, try these commands:```

## Multimedia Codecs
cd /tmp
wget http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
sudo dpkg -i w32codecs_20060611-0.0_i386.deb


sudo apt-get install gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-pitfdll gstreamer0.10-gl gstreamer0.10-ffmpeg vorbis-tools lame sox ffmpeg mjpegtools
```

:mrgreen:

---

