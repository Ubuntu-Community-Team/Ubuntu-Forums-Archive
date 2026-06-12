---
title: "opengl, wine"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Foudre on 2006-10-22
any one know how to install opengl for wine, when i google it i find a bunch of other crap, so  any hints would be aweseome

---

### Post by Lord Illidan on 2006-10-22
u don't need to install opengl for wine..as wine uses the opengl already installed on your system. It would help if you tell us what you are trying to do.

---

### Post by Foudre on 2006-10-22
trying to run some games, they think onpengl isn't install, and close  as soon as i try to play (kotor2) i have xgl installed and working i know cause i'm using beryl.

---

### Post by Foudre on 2006-10-22
on a side note.. where's my comb, my hair is wet but i can't find my comb

---

### Post by bettlebrox on 2006-10-22
There is a libwine-gl package:

apt-cache show libwine-gl
Package: libwine-gl
Description: Windows API Implementation (OpenGL Module)
 This is a BETA release of Wine, the free MS-Windows API implementation.  This is still a work in progress and many applications may still not work.
 . This package contains the OpenGL and Direct3D modules that allows  Windows apps to utilize 3D acceleration.
 . Wine is often updated.

I'm not on my Ubuntu laptop at the moment, but this is available on my Debian desktop and should be in the Ubuntu archive too.

---

### Post by Foudre on 2006-10-22
says its not availible, or that has been replaced obsolete, and has been replaced by : wine

hmm, i might just try finding the windows instlalers for these things, which is basicly what i was wanting to know, if any one knows where the opengl2.0 instller for windows might be, or is it these days included in the diretx

---

### Post by Foudre on 2006-10-22
im finding myself unable to find it for download. hmm

---

### Post by Esben Kramer on 2006-10-22
When running XGL, you can't just open applications that use openGL. As far as I know, AIGLX doesn't have this problem, and if you boot in the normal Xorg-gnome mode, the games should definately work. Either use AIGLX instead, or just boot in the normal Gnome when you want to play. I know it's a hassle, but hopefully it will soon be solved.

---

### Post by opakedragon on 2008-01-13
how do you check if you have OpenGL? Also how do you check what your system specs are exactly with Ubuntu Feisty Fawn(I've had Ubuntu for a couple of months but I'm still kinda shooting in the dark as far as this goes)?

I am trying to install WoW, I have used the tutorial in the ubuntu wiki Howto but I still have uber lag at start up less than one frame and I still cant tell if I have OpenGL...

---

### Post by altonbr on 2008-01-17
Yeah, I'm having this same problem that I've never experienced before with Wine. Google Sketchup is telling me that I can't run without OpenGL installed and running...

I was trying Wine from the WineHQ (0.9.53) repositories and now I'm trying Wine from the Ubuntu repositories (0.9.46) on Ubuntu Gutsy 7.10, x86.

libwine-gl doesn't exist in the Gutsy repos.

---

### Post by b0rka7a on 2008-01-22
Help please :( I have the same problem! OpenGL is not working!

---

