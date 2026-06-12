---
title: "Installing App from Sourceforge.net"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by LinkManDX on 2006-02-10
Hi! I'm a relatively new user to Ubuntu Breezy Badger 5.10, and I want to install this program (F4L) from sourceforge.net. The program's site can be found [here]("http://f4l.sourceforge.net"). Now, It downloaded as a .tar.bz2 archive. I unzipped it to my home folder, in a directory named f4l-0.2.1. In it are a buncha files, and I have no idea what I am doing here. I think it downloaded the source. Here is a screenshot of the folder:
[IMG]http://img494.imageshack.us/img494/2844/screenshot5pl.png[/IMG]

I would like this program this program to be installed. I have a feeling it downloaded the source, and I would really appreciate some help with this. Thank you for your time.

---

### Post by Perfect Storm on 2006-02-10
You need qt dev package before you can run its make file. Also install build-essential to get the basic compiling tools

---

### Post by LinkManDX on 2006-02-10
I have installed qt3-apps-dev and build-essential, now what do I do? What program do I run with Makefile?

---

### Post by Lord Illidan on 2006-02-10
Type ```
sudo make; sudo make install
``` to begin compiling.

---

