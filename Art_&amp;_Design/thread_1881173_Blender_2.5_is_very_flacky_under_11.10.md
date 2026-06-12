---
title: "Blender 2.5 is very flacky under 11.10"
date: 2011-11-15
forum: Art &amp; Design
---

### Post by basilwatson on 2011-11-15
Its very hit and miss, sometimes works fine , more often than not it doesn't work 

problems include full screen causes program to slow right down , to an unusable speed 

linking to other drawings causes it to crash 


Ive searched but cannot find anyone with similar problems ( must have missed it, if they have ) 

any solutions  ideas anyone??

kind regards Stephen

---

### Post by Cæncel on 2011-11-16
this can be due to two things:

1.- Unity/Compiz: You may be experiencing a lag due to the effects provided by your desktop

2.- Blender: File -> User Preferences -> System -> Window Draw Method, if is set to "Automatic" (by default perhaps) Blender is provably choosing for you different drawing methods each time you start the program, try setting you drawing method to "Full" or "Tripple Buffer", but be aware that Unity may worse you experience as it depends on a tweaked Compiz configuration, also the "Overlap" method makes less usage of buffer but gets flickery when full screen

Sidenote: try using one of the pre-built binaries from Blender website, if you have Blender installed via PPA or Repositories, you may be having a broken package

---

### Post by gabrielaca on 2011-11-26
first of, reinstall, caencel is rigth, then try installing this: 

> sudo apt-get install scons g++ build-essential yasm gettext libx11-dev libxi-dev libsndfile1-dev libpng12-dev libfftw3-dev libgl1-mesa-dev libopenexr-dev libopenjpeg-dev zlib1g-dev libopenal-dev libalut-dev libvorbis-dev libjpeg62-dev libglu1-mesa-dev libsdl-dev libfreetype6-dev libsdl1.2-dev libtiff4-dev libsamplerate0 libsamplerate0-dev libavdevice-dev libtheora-dev libavformat-dev libavutil-dev libavcodec-dev libjack-dev libpython3.2 libogg-dev libfaac-dev libfaad-dev libswscale-dev libx264-dev libmp3lame-dev freeglut3-dev libglew1.5-dev libboost-all-dev subversion python3.2-dev python3.2-dbg

worked for me; im sorry idont remember who posted this code anymore, but thanks goes to him.

---

### Post by mandza on 2012-03-21
> **gabrielaca said:**
> first of, reinstall, caencel is rigth, then try installing this: 



worked for me; im sorry idont remember who posted this code anymore, but thanks goes to him.

i try to install this packages but i recive an error:

 libgl1-mesa-dev : Ba&#287;&#305;ml&#305;l&#305;klar: libgl1-mesa-glx (= 7.11-0ubuntu3) ama 7.11-0ubuntu3.1 kurulacak

libglu1-mesa-dev : Ba&#287;&#305;ml&#305;l&#305;klar: libglu1-mesa (= 7.11-0ubuntu3) ama 7.11-0ubuntu3.1 kurulacak

---

### Post by mandza on 2012-03-21
i downloaded blender directly from blender.org and run blender-softwaregl from extracted folder and now my blender is working.

---

