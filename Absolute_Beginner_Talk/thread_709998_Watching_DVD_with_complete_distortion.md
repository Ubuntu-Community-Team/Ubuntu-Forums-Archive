---
title: "Watching DVD with complete distortion"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by ubacct3 on 2008-02-28
I have a Geforce 6200 LE and watching DVD.  It's like watching distorted unsubscribed channels on TV.

When I reboot, it's back to normal.

This happens regardless of what type of movie player I use. 

Any suggestions?

---

### Post by talsemgeest on 2008-02-28
Take a look here: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability)

Hope this helps :)

---

### Post by jan quark on 2008-02-28
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

for the whole story see here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28restricted%29)

---

### Post by oedha on 2008-02-28
what if the compiz turned off ?

---

