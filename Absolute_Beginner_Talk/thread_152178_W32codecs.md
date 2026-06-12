---
title: "W32codecs"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by nsmith on 2006-03-29
I installed the W32 codecs on my computer and I get sound when I play mpeg files but no video.  Any help?

---

### Post by endersshadow on 2006-03-29
Try this:

```
sudo apt-get install totem-xine gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg gstreamer0.8-faac gstreamer0.8-faad libxvidcore4 lame sox ffmpeg mjpegtools vorbis-tools mpg321
```

---

### Post by nsmith on 2006-03-29
I tried that and get this message

E: Couldn't find package gstreamer0.8-lame

---

### Post by endersshadow on 2006-03-29
What's your /etc/apt/sources.list file look like? (gedit /etc/apt/sources.list -- print the output here)

---

### Post by nsmith on 2006-03-29
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://cv.archive.ubuntu.com/ubuntu](http://cv.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://cv.archive.ubuntu.com/ubuntu](http://cv.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://cv.archive.ubuntu.com/ubuntu](http://cv.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://cv.archive.ubuntu.com/ubuntu](http://cv.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://cv.archive.ubuntu.com/ubuntu](http://cv.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://cv.archive.ubuntu.com/ubuntu](http://cv.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://cv.archive.ubuntu.com/ubuntu](http://cv.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://cv.archive.ubuntu.com/ubuntu](http://cv.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by endersshadow on 2006-03-29
Try this:

```
sudo gedit /etc/apt/sources.list
```

Then, add the following line to the bottom:

```
deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
```

Then, save and close it, and run:

```
sudo apt-get update
sudo apt-get install totem-xine gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg gstreamer0.8-faac gstreamer0.8-faad libxvidcore4 lame sox ffmpeg mjpegtools vorbis-tools mpg321
```

---

