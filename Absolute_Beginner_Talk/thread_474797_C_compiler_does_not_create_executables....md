---
title: "C compiler does not create executables..."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-06-15
Hai everyone,


I am a beginner in using ubuntu and I dont know how to connect to the internet. I have tried everything i know 
but nothing works.I have dual booted the computer with XP and i have downloaded GNOME ppp. I tried to install
it using the terminal but in vain. I have a dialup connection to the internet and my modem is installed correctly.
When i type "./configure" in the terminal some statements appear which is followed by
           "Error: C compiler cannot create executables. See configure.log for details"

Somebody please help me!!!!!!!!

---

### Post by Tomosaur on 2007-06-15
Ok well first of all, the answer is that you need to download the build-essential package (which contains everything you need to compile). The problem is that you have no internet connection, which means this is impossible, and is really a very bad oversight by the Ubuntu developers.

This page has a debian package for Gnome-PPP, which removes the need to compile stuff.
[http://packages.debian.org/unstable/net/gnome-ppp](http://packages.debian.org/unstable/net/gnome-ppp)

You may need to download the dependencies and install those aswell. Once you have downloaded the .deb file, simply double click on it to start the installer.

---

