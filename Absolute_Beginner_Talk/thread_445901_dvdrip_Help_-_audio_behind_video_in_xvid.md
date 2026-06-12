---
title: "dvd::rip Help - audio behind video in xvid"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by robertpolson on 2007-05-16
When the dvd ripping is done, in the .avi file the audio is behind the video
stream.  I tried both, with PSU core enabled and disabled.

Attached is a screenshot of how the settings look. Please help.

[[IMG]http://img373.imageshack.us/img373/9573/dvdripsettingstp9.jpg[/IMG]](http://imageshack.us)

---

### Post by netwerx on 2007-05-16
The only program ive ever used to do what your doing is dvd2avi for linux.

check here for more info...
[http://dvd2avi.sourceforge.net/](http://dvd2avi.sourceforge.net/)

---

### Post by robertpolson on 2007-05-16
Avidemux does a good job for me. It is just that I really want to know what I am doing wrong with dvd::rip so that the audio is behind the video stream.

[http://avidemux.berlios.de/index.html](http://avidemux.berlios.de/index.html)

As for dvd2avi, there is no debian package on their site and it is not in repos. I do not know how to install otherwise.

---

### Post by vanadium on 2007-05-16
Perhaps there is a delay for the ac3 that is not taken into account when muxing the mp3. You can mux the AVI again using Avidemux. Specify a value for "Shift" to account for the delay in the audio. You may need to do some trial and error to find the correct delay. Try in steps of 50 ms. 

As another comment, you are producing bad quality. You are transcoding an NTSC DVD without any interlacing or reverse telecine. If the DVD is a movie, you should do reverse telecine. This creates 23.9 fps progressive frames from your 29.9 fps source. Less frames that are easier to encode (no interlacing patters) will make for a tremendous better video quality at the same bitrate.

If your material comes from a video camera or is recorded from a TV show, it will be truly interlaced material. There, you need to apply a deinterlace algorithm, which converts your 29.9 fps source to 29.9 non-interlaced frames.

Probably, there is also an option to delay the audio in DVD:RIP, which you would set on beforehand. However, I am not yet familiar with video conversion in Linux.

---

### Post by dannyboy79 on 2007-05-16
> **robertpolson said:**
> Avidemux does a good job for me. It is just that I really want to know what I am doing wrong with dvd::rip so that the audio is behind the video stream.

[http://avidemux.berlios.de/index.html](http://avidemux.berlios.de/index.html)

As for dvd2avi, there is no debian package on their site and it is not in repos. I do not know how to install otherwise.

it would be a shame if you never gave a try to installing from source. you can't always count on stuff being in synaptic. here's a guide to installing anything in linux, from .rpm's to tarred source files. good luck. 

PS. it's not hard and most all source files come with an install text file for you to read and know how to install it. it basically boils down to you needing to compile it for your linux distro and environment I beleive, hence these three commands are almost a must in linux.

./configure
make
checkinstall (or just "make install" but the checkinstall will create  a .deb for easy uninstallation. you need to install checkinstall to be able to use it)

---

### Post by robertpolson on 2007-05-17
I'll just play around with Avidemux and will learn more about codecs and filters. I like it. It does the job well.

Thanks for the input though.

---

