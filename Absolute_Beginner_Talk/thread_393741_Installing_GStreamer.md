---
title: "Installing GStreamer"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by coollikestevie on 2007-03-26
When i try to install GStreamer tarball, i run ./configure and it comes up with this

> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking nano version... 0 (release)
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables



in my config.log it shows this:

> configure:1665: checking for a BSD-compatible install
configure:1720: result: /usr/bin/install -c
configure:1731: checking whether build environment is sane
configure:1774: result: yes
configure:1839: checking for gawk
configure:1868: result: no
configure:1839: checking for mawk
configure:1855: found /usr/bin/mawk
configure:1865: result: mawk
configure:1875: checking whether make sets $(MAKE)
configure:1895: result: yes
configure:2075: checking nano version
configure:2081: result: 0 (release)
configure:2102: checking whether to enable maintainer-specific portions of Makefiles
configure:2111: result: no
configure:2133: checking build system type
configure:2151: result: i686-pc-linux-gnulibc1
configure:2159: checking host system type
configure:2173: result: i686-pc-linux-gnulibc1
configure:2297: checking for style of include used by make
configure:2325: result: GNU
configure:2396: checking for gcc
configure:2412: found /usr/bin/gcc
configure:2422: result: gcc
configure:2666: checking for C compiler version
configure:2669: gcc --version </dev/null >&5

Is there some easier way to install GStreamer? all i want to do is play mp3s! is there a way of getting a C compiler which can create executables?

---

### Post by seshomaru samma on 2007-03-26
you need the gcc and build-essential package to build a tar by yourself
however there is a much easier way, run this in a terminal:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
```

---

### Post by seshomaru samma on 2007-03-26
you need the gcc and build-essential package to build a tar by yourself
however there is a much easier way, run this in a terminal:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
```

(you need to enable the universe and multiverse repos for it to work)

---

### Post by coollikestevie on 2007-03-26
Hey thanks seshomaru! the first two worked.. the third one gave me this:

> stevieb@utnubu:~$ sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


what are universe and multiverse repos and how do you enable them?

---

### Post by Outrunner on 2007-03-26
An easy way to do it is to go in Synaptic(System->Administration->Synaptic Package Manager), go to Settings->Repositories and tick the boxes next to the universe and multiverse repos.

---

### Post by coollikestevie on 2007-03-26
oh ok. they were already checked.

another way of getting there is..

System->Administration->System Sources

thanks for your help

---

