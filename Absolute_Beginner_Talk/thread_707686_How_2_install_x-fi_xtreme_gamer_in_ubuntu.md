---
title: "How 2 install x-fi xtreme gamer in ubuntu?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by blaze2k on 2008-02-25
So im a complete noob , my only linux experience is with openwrt (linux based os 4 routers)
I installed ubuntu and i have no sound... the only driver i found was the 64bit version on creative.com . Can anyone hellp me with any advice how to install my x-fi xtreme gamer?

---

### Post by terry_gardener on 2008-02-25
.

---

### Post by terry_gardener on 2008-02-25
try this site to download the driver. 

[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

make sure that you have installed the build-essential package first. 

you will also have to fix the sound in firefox use instruction on the post

[http://ubuntuforums.org/showthread.php?t=687220](http://ubuntuforums.org/showthread.php?t=687220)

hope this helps

---

### Post by blaze2k on 2008-02-26
Her's what i done.
1.Donwlonad driver oss-linux_v4.0-1013_i386.deb
2. Installed  build-essential
3.installed driver
4.syste/preferences/sound i was trying to test the sound after selecting OSS and it dosent seem to find any device coz thers no mixer to select.

This is what i get: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

---

### Post by iBoniek on 2008-02-27
have same problem. I can see my x-fi on hardware monitor but I can't see it in soundmanager

---

