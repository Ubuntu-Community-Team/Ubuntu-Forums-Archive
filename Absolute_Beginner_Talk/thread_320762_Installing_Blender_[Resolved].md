---
title: "Installing Blender? [Resolved]"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Jack the R on 2006-12-17
There's three Linux i386 versions - does anyone have a clue what the difference between "static" and "dynamic" is?

---

### Post by aysiu on 2006-12-17
Do you still have your Kubuntu computer hooked up to the internet? If so, you can **[enable extra repositories](http://www.psychocats.net/ubuntu/sources)** and then paste this command into the terminal to install Blender: ```
sudo aptitude update && sudo aptitude install blender
``` If not, use your connected PC to download these files:
[http://mirrors.kernel.org/ubuntu/pool/universe/b/blender/blender_2.42a-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/b/blender/blender_2.42a-1ubuntu1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-3_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/f/ffmpeg/libavcodec0d_0.cvs20060823-3.1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/f/ffmpeg/libavcodec0d_0.cvs20060823-3.1ubuntu1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/f/ffmpeg/libavformat0d_0.cvs20060823-3.1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/f/ffmpeg/libavformat0d_0.cvs20060823-3.1ubuntu1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/libd/libdc1394/libdc1394-13_1.1.0-3ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libd/libdc1394/libdc1394-13_1.1.0-3ubuntu1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.10-13_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.10-13_i386.deb)

Copy those to your Kubuntu computer's desktop and type these commands into the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by Jack the R on 2006-12-17
What version is that?

---

### Post by reiatzu on 2006-12-17
You appear to be quite lazy, Jack the R.
The version of Blender is 2.42a

---

### Post by Jack the R on 2006-12-17
Mmm, thanks.

How can you tell by the links he's posted what version the links install?

---

### Post by Jack the R on 2006-12-17
Nevermind, saving the link displays the entire file name and shows "2.42a," which is replaced by a bunch of periods here in the thread.  Now I know what to look for.

---

### Post by maaronB on 2006-12-17
> **Jack the R said:**
> does anyone have a clue what the difference between "static" and "dynamic" is?

From the Blender Website
> Static Linux version is for systems without HW OpenGL

---

### Post by Jack the R on 2006-12-17
Got it running!  Thanks again!

---

