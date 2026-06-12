---
title: "dell inspiron sound"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Leafx on 2008-03-19
i have a dell inspiron 1720 and i can not get my sound to work. it is just stuck on mute i guess, i can't access sound control and the restricted drivers doesnt list my audio on there only video and wireless.. any help getting this started? i would like to start watching movies or listen to music on my laptop. also what is gstreamer?

---

### Post by donnyblaze1 on 2008-03-19
Fire up your favorite terminal and do the following:
```

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2

tar xvpjf alsa-driver-1.0.15rc1.tar.bz2

cd alsa-driver-1.0.15rc1

./configure --with-cards=hda-intel

make

sudo make install
```

This of course assumes that you have the development requirements installed.  If it gives you an error...
```
sudo apt-get install gcc
```
should do the trick.

Good luck!

---

### Post by Leafx on 2008-03-19
i got it working, great, thanks again guys

---

