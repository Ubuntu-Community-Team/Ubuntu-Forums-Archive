---
title: "Sound in Totem/Xine"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by gnama on 2006-11-09
I need help with getting the codec Windows Media Audio v2 for my box. Thanks!

---

### Post by gnama on 2006-11-10
Help?

---

### Post by digby on 2006-11-10
Make sure you have enabled the [multiverse]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories") repository.

Then, try these commands:```

## Multimedia Codecs
cd /tmp
wget http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
sudo dpkg -i w32codecs_20060611-0.0_i386.deb


sudo apt-get install gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-pitfdll gstreamer0.10-gl gstreamer0.10-ffmpeg vorbis-tools lame sox ffmpeg mjpegtools
```

---

