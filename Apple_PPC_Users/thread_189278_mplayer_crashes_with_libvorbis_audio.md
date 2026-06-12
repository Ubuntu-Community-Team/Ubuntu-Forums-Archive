---
title: "mplayer crashes with libvorbis audio"
date: 2006-06-05
forum: Apple PPC Users
---

### Post by Focx on 2006-06-05
Hi,

I installed xubuntu on my 500mhz ibook, works perfectly, but after installing mplayer it crashed when opening ogm or mkv containerfiles that contain audio that needs the libvorbis library. With alsa it crashes leaving a ao2_init error, with oss it says default_audio error. Other files using mp3 it is able to play, but only with oss as a driver.

I checked with vlc - it is able to play the file correctly with audio and video, while xine does not find the proper plugins and xmms is not able to load the libvorbisfile.so and can't play ogg vorbis files.

Any ideas?

---

### Post by Focx on 2006-06-06
Hi,

some new idea: I get the error message "Illegal instruction", and get warned about a possible problem with mplayers cpu detection mechanism, or it being compiled for the wrong platform.

Yet, I can play non-ogg vorbis files perfectly... and ogg vorbis files perfectly in other players, so I'm not sure if this is really the problem.

meanwhile, vlc is just too slow to play the files :/

---

### Post by Focx on 2006-06-09
If anyone could try to help me, I filed a bug at [https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/48941]("https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/48941") ...

---

