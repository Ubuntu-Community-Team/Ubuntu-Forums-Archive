---
title: "Tarballs"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Mitchlb on 2008-01-22
Before anyone goes telling me: "Mitchell, tarballs are not the way", let me explain my situation. I have an ubuntu run system that can't go online. It is an older system without a built in network card. I have a 1ghrtz wireless connection in my house, but it can't be accessed. I know of no network cards that have an ubuntu installation available to them. My system is a pentium 3, 50gb, sony. (I'm happy to buy something if i need too (and i probably do), i just need to know what to get)

I'm stuck downloading tarballs from an xp run system and loading them on my Ubuntu run system. Recently i tried to get vlc media player up and running. 

I have never worked with tarballs before. I want to install Vlc Media player, and i don't know how to install tarballs. Here - [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html), i downloaded the vlc media player. I have a standard installation of Ubuntu 7.10, with no extra packages. Can someone walk me through the installation using the "VLC source code tar.gz" file. You can download it yourself and tell me how you installed it, or if you have great experiance with tarballs that can be good too.

If i need any packages, i have a system on which i can download them. (An xp run system) (Forgive me, i'm only just starting the switch to Ubuntu). And i can transfer them but, unfortunitely, you would have to walk me through that installation as well. Please Help :confused:


[SIZE="1"]I have posted a very similair message a few times now, and have had no luck.[/SIZE]

---

### Post by wolfen69 on 2008-01-22
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9358-howto-install-software-readme.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9358-howto-install-software-readme.html)

---

### Post by ntowakbh on 2008-01-22
> **Mitchlb said:**
> Before anyone goes telling me: "Mitchell, tarballs are not the way", let me explain my situation. I have an ubuntu run system that can't go online. It is an older system without a built in network card. I have a 1ghrtz wireless connection in my house, but it can't be accessed. I know of no network cards that have an ubuntu installation available to them. My system is a pentium 3, 50gb, sony. (I'm happy to buy something if i need too (and i probably do), i just need to know what to get)

I'm stuck downloading tarballs from an xp run system and loading them on my Ubuntu run system. Recently i tried to get vlc media player up and running. 

I have never worked with tarballs before. I want to install Vlc Media player, and i don't know how to install tarballs. Here - [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html), i downloaded the vlc media player. I have a standard installation of Ubuntu 7.10, with no extra packages. Can someone walk me through the installation using the "VLC source code tar.gz" file. You can download it yourself and tell me how you installed it, or if you have great experiance with tarballs that can be good too.

If i need any packages, i have a system on which i can download them. (An xp run system) (Forgive me, i'm only just starting the switch to Ubuntu). And i can transfer them but, unfortunitely, you would have to walk me through that installation as well. Please Help :confused:


[SIZE="1"]I have posted a very similair message a few times now, and have had no luck.[/SIZE]

First extract it, then open a terminal and cd into the directory for VLC source code then run the configure script 
```
./configure
```

then compile it
```
make
```

install it
```
sudo make install
```

make clean
```
make clean
```

You will probably need the build dependency packages for VLC though....I'll see if I can find what those are.

---

### Post by Paul820 on 2008-01-22
Is your ubuntu install on the same computer as the windows one? If it is you can use **ntfs-3g** to get read and write access to the windows drive and grab the files off of it. To build source code you are going to have to get hold of **build-essential** and any of the dependencies that the source that you are building relies on. This can amount to a lot of dependencies because one file usually relies on another and so on.

---

### Post by Mitchlb on 2008-01-22
ntowakbh:

It worked until **make**

That's actually what i did orgionally. I hope you find the things i need. Thank you for really paying attention to my message.

---

### Post by Mitchlb on 2008-01-22
Paul820:

No. It's a different computer.

---

### Post by ntowakbh on 2008-01-22
> **Mitchlb said:**
> ntowakbh:

It worked until **make**

That's actually what i did orgionally. I hope you find the things i need. Thank you for really paying attention to my message.

```
ntowakbh@compone:~$ sudo apt-get build-dep vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dh-buildinfo firefox-dev liba52-0.7.4-dev libarts1-dev libartsc0-dev libaudio-dev libavc1394-dev libavcodec-dev libavformat-dev
  libavutil-dev libcaca-dev libcdio-dev libcucul-dev libcupsys2-dev libdc1394-13-dev libdirectfb-dev libdirectfb-extra libdts-dev
  libdvbpsi4-dev libdvdnav-dev libdvdread-dev libebml-dev libfribidi-dev libggi2 libggi2-dev libgii1 libgii1-dev libgii1-target-x libglide2
  libglide2-dev libglu1-mesa-dev libgsm1-dev libimlib2-dev libiso9660-dev liblircclient-dev liblivemedia-dev libltdl3-dev libmatroska-dev
  libmodplug-dev libmpcdec-dev libmpeg2-4-dev libnotify-dev libnspr4-dev libnss3-dev libpostproc-dev libqt3-headers libqt3-mt-dev
  libraw1394-dev libsdl-image1.2-dev libsdl1.2-dev libsmbclient-dev libspeex-dev libsvga1 libsvga1-dev libsysfs-dev libtar-dev
  libtheora-dev libungif4-dev libvcdinfo-dev libxosd-dev libxv-dev nasm qt3-dev-tools x11proto-video-dev xlibmesa-gl-dev
0 upgraded, 65 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.9MB of archives.
After unpacking 91.2MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

Some how, I don't think you would want to manually download the packages listed to build it...

Have you tried looking for a deb?

---

### Post by Mitchlb on 2008-01-22
Yes. [www.getdeb.net](www.getdeb.net) 

Wasn't able to find anything.

---

### Post by spiderbatdad on 2008-01-22
have you installed build-essential? You can do so via synaptic package manager...then your ubuntu cd will be requested.BTW i use a cisco aironet wireless card...worked out of the box.

---

### Post by S15_88 on 2008-01-22
hit up the terminal and do: sudo apt-get build-essentials

---

### Post by Mitchlb on 2008-01-23
So the cisco aironet wireless card has a linux installation or is it a plug n' go. Also people (NO INTERNET ACCESS).

---

### Post by Mitchlb on 2008-01-23
I have an 802.11g connection if that helps.

---

