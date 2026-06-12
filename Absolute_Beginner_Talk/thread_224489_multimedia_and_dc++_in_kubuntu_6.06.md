---
title: "multimedia and dc++ in kubuntu 6.06"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-07-28
guys...

i just switch from ubuntu 5.10 to kubuntu 6.06.

1)how can i configure to play movies and listen to music?

2)what is the application in kubuntu for dc++?

thx guyz~~

---

### Post by Jagot on 2006-07-28
1.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by penguinKabuki on 2006-07-28
===========
Kubuntu 6.06 LTS (Dapper Drake), 5.10 (Hoary Hedgehog) 
 Install the package flashplugin-nonfree 
Note to Kubuntu Users: Konqueror does not auto-detect Flash. There are a few steps you must take: 
 In the menu bar of konqueror, click "Settings" (next to Help) > "Configure Konqueror" 
 Scroll down the side to plugins 
 Click "Scan for new plugins" 
 Flash should now work with konqueror.
================

where is konqueror?
what it means by....."in the menu bar of konqueror.."?

---

### Post by penguinKabuki on 2006-07-28
==========
Kubuntu 6.06 LTS (Dapper Drake) 
 Install libxine-extracodecs. 
 To add mp3 support to K3b, install libk3b2-mp3. 
 To add mp3 support to JuK, install libakode2-mpeg and libarts1-mpeglib. 
 To add mp3 support for use with K3b, install libk3b2-mp3. 
 Video thumbnails in Konqueror -- install libarts1-xine. You can turn this functionality on and off through Konqueror's menu View->Preview->Video files. 
Audio Previewing -- The Kubuntu file manager Konqueror can preview sound files if you hover your mouse pointer over the file (this can be enabled in Konqueror's menu under View->Preview->Sound files). If you would like to add this functionality for use with mp3 files, install libarts1-mpeglib. 
=============

how can i install libxine-extracodecs.?
use the terminal?

---

### Post by Perfect Storm on 2006-07-28
terminal:

```
sudo apt-get install <insert the thing you want tto install here>
```

Just make sure that your sourcelist is set up first.

---

### Post by penguinKabuki on 2006-07-28
============
root@penguin-desktop:~# sudo apt-get install libk3b2-mp3
Reading package lists... Done
Building dependency tree... Done
Package libk3b2-mp3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libk3b2-mp3 has no installation candidate
root@penguin-desktop:~# sudo apt-get install libakode2-mpeg
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libakode2-mpeg
root@penguin-desktop:~# sudo apt-get install libarts1-mpeglib
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libarts1-mpeglib
root@penguin-desktop:~# sudo apt-get install  libk3b2-mp3
Reading package lists... Done
Building dependency tree... Done
Package libk3b2-mp3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libk3b2-mp3 has no installation candidate
root@penguin-desktop:~# sudo apt-get install  libarts1-xine
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libarts1-xine
root@penguin-desktop:~# sudo apt-get install libarts1-mpeglib
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libarts1-mpeglib
===============

and...my penguin still silent :sad:

---

### Post by gingermark on 2006-07-28
What you are doing logged in as root I don't know, but read this: [http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

It explains how to install software in Kubuntu.

EDIT: Oh, and the [Kubuntu Desktop Guide](https://help.ubuntu.com/kubuntu/desktopguide/C/index.html) is probably a decennt place to start too.

---

### Post by penguinKabuki on 2006-07-28
emmm....
i dont want to install software...
i already have the amarok....the kaffeine....but....when i play a files .mp3 ....it dont work...it just keep silent.no sound at all.
really sad.....i miss my song...:sad:

---

### Post by Jagot on 2006-07-28
You may well have Amarok and Kaffeine but in a default installation they cannot play mp3 files by themselves - you need to install the correct codecs to do so:

[https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59](https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59)

---

### Post by gingermark on 2006-07-28
> **penguinKabuki said:**
> emmm....
i dont want to install software...
i already have the amarok....the kaffeine....but....when i play a files .mp3 ....it dont work...it just keep silent.no sound at all.
really sad.....i miss my song...:sad:
Ok, my bad. The link I posted teaches you how to install **stuff**.

You need to install **stuff** to get restricted formats to work.

But you don't understand the other links people have given you.

So, we need to go back to basics, so read the link I gave you. EDIT: Including the part about [Enabling extra repositories](http://psychocats.net/ubuntu/sources.php).

---

