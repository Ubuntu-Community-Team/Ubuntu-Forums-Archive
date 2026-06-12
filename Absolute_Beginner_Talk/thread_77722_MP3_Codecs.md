---
title: "MP3 Codecs"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by daoc on 2005-10-17
Hey guys, I installed Ubuntu 5.04 yesterday from a mate's disc, and the in-built media player doesnt have the mp3 codecs, i was wondering where could i get them from and cud ya help me install them, im new 2 linux. been with windows since i was a child, and was recently introduced 2 linux when most my lecturers use it.

Thanks

---

### Post by matid on 2005-10-17
Look it up in [Ubuntu Guide](http://ubuntuguide.org/).
It's answered under '[How to install Multimedia Codecs?'](http://ubuntuguide.org/#codecs)

---

### Post by colly3 on 2005-10-17
a lot of info about multimedia can be found on this page
[http://ubuntuguide.org/](http://ubuntuguide.org/)
it's a unofficial starter guide, and it helped me to install an mp3 codec.

---

### Post by daoc on 2005-10-17
thanks guys

linux users are so much more friendly then vindows' users

---

### Post by daoc on 2005-10-17
hey guys, ive tried 2 install off tht page u said, but all i was getting at the end of it was:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

n e suggestions?

---

### Post by John.Michael.Kane on 2005-10-17
@daoc look here [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs)
[https://wiki.ubuntu.com/FreeFormats?highlight=%28formats%29%7C%28free%29](https://wiki.ubuntu.com/FreeFormats?highlight=%28formats%29%7C%28free%29)

these should be in synaptic
 install gstreamer0.8-plugins
 install gstreamer0.8-lame
 install gstreamer0.8-ffmpeg
 install lame
 install sox
 install ffmpeg
 install mjpegtools
 install vorbis-tools

This should get you going

side note daoc mirrormax is not being used for Hoary. used this for any backports you need when using Hoary.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

---

