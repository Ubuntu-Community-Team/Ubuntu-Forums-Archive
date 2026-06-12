---
title: "possibly mpeg mpg codecs?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by modulistic_terror on 2007-02-02
all of my video transfers are on mpg or mpeg format and i keep getting told i need the codecs to play them but i cant find them anywhere. could anybody please help?

---

### Post by bbukh on 2007-02-02
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

---

### Post by modulistic_terror on 2007-02-02
garry@garry-desktop:~$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
> gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
> gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.10-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-ffmpeg has no installation candidate
 


that is all that im being told.

---

### Post by 23meg on 2007-02-02
Make sure [the Universe and Multiverse repositories are enabled]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html").

---

### Post by modulistic_terror on 2007-02-02
garry@garry-desktop:~$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
> gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
> gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
Reading package lists... Done
Building dependency tree... Done
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


i think were getting closer.

---

### Post by 23meg on 2007-02-02
For w32codecs, see [this]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs").

---

### Post by modulistic_terror on 2007-02-02
i did as the instructions said but theyre still not playing. 
do i have to manually configure the codecs?

---

### Post by 23meg on 2007-02-03
Try refreshing your gstreamer codec registry with```
rm -rf ~/.gstreamer-0.10
gst-inspect-0.10
```

---

