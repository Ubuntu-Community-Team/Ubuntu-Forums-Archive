---
title: "Rhythmbox Music Player"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2007-11-23
I opened the Rhythmbox music player and then clicked on "New Internet Radio Station" to add a new station with no problem but when i selected the new radio station and clicked on play i am informed that: 

You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

Could someone tell me how i might install the necessary plugins please. Big thanks

---

### Post by Bobrm2 on 2007-11-23
I too need information concerning the pluging??
Bob

---

### Post by AlexMono94 on 2007-11-24
Open the terminal and type:

```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg
```

That will install codecs  for basically all multimedia formats such as WMA and MP3 allowing you to listen to WMA and MP3 streams.

---

### Post by bagoomba on 2007-11-25
I ran that, but get an error:

Package gstreamer0.10-plugins-bad is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gstreamer0.10-plugins-good gstreamer0.10-plugins-base
E: Package gstreamer0.10-plugins-bad has no installation candidate

Sorry if this is a newbie problem, but I am what I am!  :)

---

### Post by Incense on 2007-11-25
Are you in gutsy? You can install the following package to get most codecs. 

```
sudo apt-get install ubuntu-restricted-extras
```

This will install (AFAIK)

> cabextract flashplugin-nonfree gsfonts-x11 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse jackd java-common liba52-0.7.4 libavcodec1d libavutil1d libcdaudio1 libdvdread3 libfaac0 libfaad2-0 libfreebob0 libgsm1 libid3tag0 libjack0 liblame0 libltdl3 libmad0 libmjpegtools0c2a libmms0 libmp4v2-0 libmpcdec3 libmpeg2-4 libqt3-mt libquicktime1 libsidplay1 libsoundtouch1c2 libx264-54 libxvidcore4 msttcorefonts odbcinst1debian1 qjackctl sun-java6-bin sun-java6-jre sun-java6-plugin ubuntu-restricted-extras unixodbc unrar

---

### Post by Paul86fxr on 2008-01-10
worked for me!!! thanks once again, you guys are awesome.

Paul

---

### Post by mihai.ile on 2008-01-11
hopefully in the near fututre rhythmbox will ask for the codecs to install automatically as Totem does.

---

