---
title: "Totem encoders"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by cloucas on 2006-01-15
Can someone tell me how to configure Totem to play wmv, mpg, avi and other popular video formats?  I keep getting an error that I need to install plugins as the necessary decoders are missing.


Thanks in Advance

---

### Post by Perfect Storm on 2006-01-15
enable universe and multiverse in your sourcelist and add PLF. Then:

```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg gstreamer0.8-plugins-multiverse w32codecs lame sox ffmpeg mjpegtools vorbis-tools avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin avifile-win32-plugin avifile-xvid-plugin
gst-register-0.8

```

My recommendation/favor is VLC. I think you should try it out :)



For DVD:

```

sudo apt-get install libdvdcss2

```

---

