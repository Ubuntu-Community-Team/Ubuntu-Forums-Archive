---
title: "[SOLVED] problem to install libxine1"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by My_Ausweis on 2007-12-02
Dear All

I have problem to install libxine1. I already download, when i tried to install this package an error occured with text " not dependencies libxine1"

I confuse why this happen, because this is libxine1. the package that i use is libxine1_1.1.7-1ubuntu1_i386.deb.This file can be found when u search use packages.ubuntu.com/libxine1 and i use ubuntu 7.10 alternate.

Anyone can help me ? 

and also anyone know where to find imlib1 ?


Thx

L.M

---

### Post by forestpixie on 2007-12-02
how are you trying to install libxine1 - Gdebi should deal with dependencies

can find - gdk-imlib1, but not imlib1 - [http://packages.ubuntu.com/gutsy/oldlibs/gdk-imlib1](http://packages.ubuntu.com/gutsy/oldlibs/gdk-imlib1)

---

### Post by My_Ausweis on 2007-12-02
Dear

Here the step

First I download libxine1 from Internet after that i brought it home and put in my hard drive, 

How i try to install that package :

I point it using mouse and double clik that mouse, i try to several package it worked but not for libxine1, 

the error shown : not dependecies libxine1,


Any one know how to solve this problem ?


Thx

L.M

---

### Post by forestpixie on 2007-12-02
what happens if you do it from the terminal

```
sudo apt-get install libxine1
```

if it doesn't install please paste the error you get

---

### Post by My_Ausweis on 2007-12-02
the error shown when i tried to use terminal

sudo apt-get install libxine1 is "couldn't find the package libxine1" 

and i also tried to

sudo apt-get install libxine1_1.1.7-1ubuntu1_i386.deb

and the error shown

couldn't find the package libxine1_1.1.7-1ubuntu1_i386.deb

i'm affraid this is wrong packet with name libxine1

any suggestion or alternative link for libxine1 ?

Thx

L.M

---

### Post by corney91 on 2007-12-02
Are you connected to the internet?
What happens if you type:```
sudo apt-get update
```

---

### Post by Partyboi2 on 2007-12-02
I think libxine1 is found under gusty backports. You will need to have this enabled under 'Software Sources' then you should be able to:
```
sudo apt-get install libxine1
```[http://packages.ubuntu.com/gutsy-backports/libs/index.ja.html](http://packages.ubuntu.com/gutsy-backports/libs/index.ja.html)

---

### Post by My_Ausweis on 2007-12-02
Sorry i don't have internet connection, so i download it through cyber cafe

Do you have that link, so i can update by downloading that file ?

Thx

L.M

---

### Post by My_Ausweis on 2007-12-02
I think libxine1 is found under gusty backports. You will need to have this enabled under 'Software Sources' then you should be able to:


How to enable under software sources ?

---

### Post by monte48lowes on 2007-12-02
Here is the libxine1 package on the ubuntu gutsy packages website:

[http://packages.ubuntu.com/gutsy/libs/libxine1]("http://packages.ubuntu.com/gutsy/libs/libxine1")

You can find all of the packages available from the repositories here:

[http://packages.ubuntu.com/gutsy/allpackages]("http://packages.ubuntu.com/gutsy/allpackages")

For each package it lists the dependancies. How do you know what you already have installed?

```
dpkg -l > installedPacks.txt
```

Copy 'installedPacks.txt' to your portable hard drive. Then you can check which dependancies you already have installed.

Mike

---

### Post by forestpixie on 2007-12-02
Make sure all the boxes are ticked in software sources, close and reload when it tells you should do it, then install it

```
sudo apt-get install libxine1
```

though I don';t know how you'll achieve that without an internet connection.

I think [this]("http://www.ubuntu-hr.org/proba.php") site will tell you which dependencies there are so you can get them all from the cyber cafe if you need to

---

### Post by My_Ausweis on 2007-12-02
Where can i find software sources that should be ticked. Because i'm new in ubuntu.

I've tried to install  gutsy backbourne packet, and the end of the point is always libxine1

Thx

L.M

---

### Post by Partyboi2 on 2007-12-03
Have you tried double clicking on the libxine1 package that you already have from the internet cafe. Then when the package installer opens. Have a look underneath the package name at "Status"  it will tell you how many other packages are required for libxine1 to work. You will see a button marked "details" click on that and another window will open with a list of packages that are not installed on your system that you need to install to get libxine1 to work. Copy them down and go back to the internet cafe and download those packages. Then install them first before trying to install libxine1
Have a look at screen shots.

---

### Post by My_Ausweis on 2007-12-04
but the display shown for detail that you've shown (by attachment) is different with me

if it needs other file to be installed first the error :

not dependecies (file name)

and the detail shown :

just name of the package and email of the creator

so how can i solve the problem to install libxine1 ?

Thx

L.M

---

### Post by My_Ausweis on 2007-12-05
Here the information from the package that i already extract

Package: libxine1
Source: xine-lib
Version: 1.1.7-1ubuntu1
Architecture: i386
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Reinhard Tartler <siretart@tauware.de>
Installed-Size: 5528
Depends: libasound2 (>> 1.0.14), libc6 (>= 2.5-5), libdirectfb-0.9-25, libflac8, libgl1-mesa-glx | libgl1, libglu1-mesa | libglu1, libmagick9, libmng1 (>= 1.0.3-1), libmodplug0c2 (>= 1:0.7-4.1), libmpcdec3, libogg0 (>= 1.1.3), libpulse0, libsdl1.2debian (>= 1.2.10-1), libsmbclient (>= 3.0.2a-1), libspeex1 (>= 1.1.8), libstdc++6 (>= 4.2-20070516), libtheora0, libvorbis0a (>= 1.1.2), libx11-6, libxcb-shape0, libxcb-shm0, libxcb-xv0, libxcb1, libxext6, libxine1 (<< 1.1.8), libxine1 (>= 1.1.7), libxinerama1, libxv1, libxvmc1, zlib1g (>= 1:1.2.1)
Recommends: libxine1-ffmpeg, libxine1-doc | libxine-doc
Suggests: libxine1-plugins, xine-ui, gxine
Section: libs
Priority: optional

---

### Post by Partyboi2 on 2007-12-05
I tried to install libxine1 on a clean install of Gusty and these were the packages that I required to get libxine1 installed. This may work for you, then again it may not.
Make sure the following packages are installed
libmodplug0c2
libmpcdec3
libpulse0
libxcb1
libxcb-shape0
libxcb-shm0
libxcb-xv0
libxvmc1
You can check by typing this in a terminal:
```
dpkg -l  libmodplug0c2 libmpcdec3 libpulse0 libxcb1 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxvmc1

```If they are installed the output will display something like this:

```
ii  libmodplug0c2             1:0.7-5.2ubuntu1          shared libraries for mod music based on ModPlug
ii  libmpcdec3                1.2.2-1build1             Musepack (MPC) format library
ii  libpulse0                 0.9.6-1ubuntu2            PulseAudio client libraries
```if any of the packages are not installed it will list something like this:

```
 libpulse0               <none>                    (no description available)
```The ones that are listed as not installed you will need to download and install. Here is a list of some of the packages that I needed to get. You can download from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[http://packages.ubuntu.com/gutsy/libs/libxine1](http://packages.ubuntu.com/gutsy/libs/libxine1)

libmodplug0c2_0.7-5.2ubuntu1_i386.deb
libmpcdec3_1.2.2-1build1_i386.deb
libpulse0_0.9.6-1ubuntu2_i386.deb
libxcb1_1.0-3_i386.deb
libxcb-shape0_1.0-3_i386.deb
libxcb-shm0_1.0-3_i386.deb
libxcb-xv0_1.0-3_i386.deb
libxvmc1_1.0.4-2ubuntu1_i386.debl
libxine1_1.1.7-1ubuntu1_i386.deb
(try to install them in order listed for ease, because libxcb-shape0 depends on libxcb1 to be installed first and libxine1 needs to be last)
If this does not work there is another way you can try go this link [http://packages.ubuntu.com/gutsy/libs/libxine1](http://packages.ubuntu.com/gutsy/libs/libxine1)
 and download and install all the packages that have a red dot next to them.

---

### Post by Partyboi2 on 2007-12-05
> **My_Ausweis said:**
> Here the information from the package that i already extract

Package: libxine1
Source: xine-lib
Version: 1.1.7-1ubuntu1
Architecture: i386
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Reinhard Tartler <siretart@tauware.de>
Installed-Size: 5528
Depends: libasound2 (>> 1.0.14), libc6 (>= 2.5-5), libdirectfb-0.9-25, libflac8, libgl1-mesa-glx | libgl1, libglu1-mesa | libglu1, libmagick9, libmng1 (>= 1.0.3-1), libmodplug0c2 (>= 1:0.7-4.1), libmpcdec3, libogg0 (>= 1.1.3), libpulse0, libsdl1.2debian (>= 1.2.10-1), libsmbclient (>= 3.0.2a-1), libspeex1 (>= 1.1.8), libstdc++6 (>= 4.2-20070516), libtheora0, libvorbis0a (>= 1.1.2), libx11-6, libxcb-shape0, libxcb-shm0, libxcb-xv0, libxcb1, libxext6, libxine1 (<< 1.1.8), libxine1 (>= 1.1.7), libxinerama1, libxv1, libxvmc1, zlib1g (>= 1:1.2.1)
Recommends: libxine1-ffmpeg, libxine1-doc | libxine-doc
Suggests: libxine1-plugins, xine-ui, gxine
Section: libs
Priority: optional
You can check if they are installed on your system
```
dpkg -l libasound2 libc6  libdirectfb-0.9-25 libflac8 libgl1-mesa-glx  libgl1 libglu1-mesa  libglu1 libmagick9 libmng1 libmodplug0c2 libmpcdec3 libogg0 libpulse0 libsdl1.2debian libsmbclient libspeex1 libstdc++6 libtheora0 libvorbis0a libx11-6 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxext6 libxine1 libxine1 libxinerama1 libxv1 libxvmc1 zlib1g

```

---

### Post by My_Ausweis on 2007-12-05
How can it will work ? Because as i saw in package dependent, it need libxine1, although this is libxine1 ?


Depends:
 libasound2 (>> 1.0.14)
 libc6 (>= 2.5-5)
 libdirectfb-0.9-25
 libflac8, libgl1-mesa-glx | libgl1
 libglu1-mesa | libglu1, libmagick9, libmng1 (>= 1.0.3-1)
 libmodplug0c2 (>= 1:0.7-4.1)
 libmpcdec3, libogg0 (>= 1.1.3)
 libpulse0, libsdl1.2debian (>= 1.2.10-1)
 libsmbclient (>= 3.0.2a-1)
 libspeex1 (>= 1.1., libstdc++6 (>= 4.2-20070516)
 libtheora0, libvorbis0a (>= 1.1.2)
 libx11-6
 libxcb-shape0
 libxcb-shm0
 libxcb-xv0
 libxcb1
 libxext6

[COLOR="Red"]
 libxine1 (<< 1.1., libxine1 (>= 1.1.7)[/COLOR]



 libxinerama1
 libxv1
 libxvmc1
 zlib1g (>= 1:1.2.1)


Thx

---

### Post by ruibernardo on 2007-12-05
To install "libxine1" in a fresh install of Ubuntu 7.10 Desktop i386 (generic kernel with Gnome) you need to download the following packages:

[http://archive.ubuntu.com/ubuntu/pool/main/libm/libmodplug/libmodplug0c2_0.7-5.2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmodplug/libmodplug0c2_0.7-5.2ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_0.9.6-1ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_0.9.6-1ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1_1.0-3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1_1.0-3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0_1.0-3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0_1.0-3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shm0_1.0-3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shm0_1.0-3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xv0_1.0-3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xv0_1.0-3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxvmc/libxvmc1_1.0.4-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxvmc/libxvmc1_1.0.4-2ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.7-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.7-1ubuntu1_i386.deb)

To find out what package files to download to install other packages in an offline computer, take a look at [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net) and this [thread/post]("http://ubuntuforums.org/showpost.php?p=3742162&postcount=11") to set it up.

---

### Post by Partyboi2 on 2007-12-05
> How can it will work ? Because as i saw in package dependent, it need libxine1, although this is libxine1 ?I see what you mean this seems to happen with the package installer. The way I got around it was to install the package manually from terminal.
Cd to where the package libxine1 can be found for example I have the package on my Desktop.
so I would type in a terminal
```
cd /home/karl/Desktop
```Once in the correct directory I would enter into terminal
```
sudo dpkg -i libxine1_1.1.7-1ubuntu1_i386.deb
```Package should be finally installed.

---

### Post by My_Ausweis on 2007-12-09
But it still need libxine1 to run libxine1

Any one know how to solve it ?

Thx

---

### Post by ruibernardo on 2007-12-09
Can you please post the output of the "dpkg -i" command line?
```
sudo dpkg -i libxine1_1.1.7-1ubuntu1_i386.deb
```

---

### Post by My_Ausweis on 2007-12-09
Thank you for all of you. it already worked

---

