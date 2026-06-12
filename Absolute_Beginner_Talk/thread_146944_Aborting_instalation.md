---
title: "Aborting instalation"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by speedbye on 2006-03-19
y0, new to ubuntu and was trying to install codecs so I could listen to music and stuff. I was using the unoffical ubuntu guide, and followed all the setps to install the codecs. I put in the terminal
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

and then it tells me all the things it will install and how much space it will will take up. Then it says
Do you want to continue [Y/n]?
I enter y, then it says 
Do you want to continue [Y/n]? y
Abort.
I dont know if im doin something wrong or what, can anyone help?

EDIT: I'm using version 5.10 for pc

---

### Post by fimbulvetr on 2006-03-19
Are you sure you're not typing an extra space, <enter> or anything before hitting yes?

It will abort if the input is anything but exactly "y". (Without the doublequotes).

If you're still having problems, do :

```
apt-get --yes <command>
```

Or do it using synaptic...

---

### Post by taurus on 2006-03-19
Why not do it the easy way and use Automatix???  

[http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix)

---

### Post by bonzodog on 2006-03-19
the mistake you made was very simple really...Linux is Case Sensitive, which means it differentiates between capitals and lower case. You need to make the 'Y' a capital one.

---

### Post by speedbye on 2006-03-19
well, thnx for everyones help
i did try a capital Y but it still didnt work
automatix worked great, but i tryed to install the ocdecs again anyway after using automatrix and it installed them without asking me if i want to proceed, but thanks for ur help

---

