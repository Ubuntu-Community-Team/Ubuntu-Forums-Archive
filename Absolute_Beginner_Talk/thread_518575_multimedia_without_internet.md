---
title: "multimedia without internet"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by bibas on 2007-08-06
i dont have internet connection on my ubuntu machine :(
is there any way to play my mp3 songs?- like downloading something from the internet then installing it on the ubuntu machine?:confused:

---

### Post by mevets on 2007-08-06
You could download the package from the Ubuntu package search. I believe you want gstreamer plugins or ffmpeg. I may be incorrect though, I honestly use automatix everytime I need codecs. You probably need more packages than just the one now that I think of it.

[http://packages.ubuntu.com/feisty/libs/gstreamer0.10-ffmpeg](http://packages.ubuntu.com/feisty/libs/gstreamer0.10-ffmpeg) and then click the link corresponding to your cpu arch. on the bottom to download.

Ubuntu-restricticed-extras has the mp3 codec in it as well as other codes for flash, java, etc. Try it if The first link is not right:
[http://packages.ubuntu.com/feisty/metapackages/ubuntu-restricted-extras](http://packages.ubuntu.com/feisty/metapackages/ubuntu-restricted-extras)

After downloading, you  can just run the package to install. Players like amarok or rhythmbox will then be able to play mp3s

---

### Post by benx009 on 2007-08-06
yes:)  i think all you have to do is download the .deb files *gstreamer0.10-ffmpeg* and *gstreamer0.10-plugins-ugly* from [packages.ubuntu.com]("http://packages.ubuntu.com/").  

if that doesn't work for you, then try downloading the following .deb packages from the same website:
[I]libxine-extracodecs
libxine1-ffmpeg
libxine1
libmodplug0c2[/I]

get them onto your linux system and then just double click on them and they should install.  the order in which you do this matters though, as some packages will rely on the installation of another.  good luck!

---

