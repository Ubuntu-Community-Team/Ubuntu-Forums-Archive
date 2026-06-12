---
title: "Playing mp3 (Installing Files Manually)"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-10-24
Hello everyone, I have tried installing mp3 playback manually in kubuntu Fiesty Fawn several times as I was not able to configure my network connection  and it worked. I dont know whether it works in others too. Please correct me if there is any mistake. Install the following in the same order. ( Right Click> Kubuntu Package Manager > Install Package )

tzdata_2007f-9_all.deb
libc6_2.5-9+b1_i386.deb
libxine1_1.1.4-2ubuntu3_i386.deb
libavutil1d_0.cvs20070307-5_i386.deb
libgsm1_1.0.10-13_i386.deb
libavcodec1d_0.cvs20070307-5_i386.deb
libmad0_0.15.1b-2.1_i386.deb
libpostproc1d_0.cvs20070307-5_i386.deb
libasound2_1.0.14a-1_i386.deb
libflac8_1.1.4-3ubuntu1_i386.deb
gcc-4.2-base_4.2-20070627-1_i386.deb
libgcc1_4.2-20070627-1_i386.deb
libstdc++6_4.2-20070627-1_i386(2).deb
libxcb1_1.0-1.1ubuntu2_i386.deb
libxcb-shape0_1.0-1.1ubuntu2_i386.deb
libxcb-shm0_1.0-1.1ubuntu2_i386.deb
libxcb-xv0_1.0-1.1ubuntu2_i386.deb
libavc1394-0_0.5.3-1build1_i386_2.deb
libraw1394-8_1.2.1-2build2_i386.deb
libxml2_2.6.29.dfsg-1_i386.deb
amarok-xine_1.4.5-0ubuntu7_i386.deb
libxine1_1.1.7-1_i386.deb
libjack0_0.103.0_i386.deb


(You can install newer versions of the above files also)


           

Note:
           Sometimes the libjack may not get installed. In such cases try to install a lower version of the same. These files are enough for mp3, wma, and playback of many other filetypes in amarok and also Kaffeine. The tzdata may or may not be installed depending on whether you are able to install libc6.


Please tell me if there is an easier way to install mp3 support. ( Considering no network connection)

---

### Post by Sturmeh on 2007-10-24
Woah dude, just use automatix! or Easybuntu, or something. xD
[B]
EDIT[/B]: Oh sorry, didn't see you had no network connection...
Perhaps automatix has an option to cache it's packages?

---

### Post by realvz on 2007-10-24
please avoid using automatix...its known to cause lot of other issues

---

### Post by erginemr on 2007-10-24
You may also give a try to "Linux Mint" in [www.linuxmint.com](www.linuxmint.com). It is basically Ubuntu with codecs (incl. mp3 playback) by default and extra / more popular software.

AFAIK, they have a KDE version too.

---

