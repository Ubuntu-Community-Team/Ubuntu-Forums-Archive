---
title: "Botched RhythmBox setup???"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by lee292 on 2007-03-20
I'm trying to get RhythmBox to play the MP3 files I've amassed in the "W' world, but I can't seem to get it to recognize MP3s.  When I was first testing Ubuntu, I was using the "Hoary Hedgehog" version and was able to download and install Bitstream0.8, and MP3 files played fine.  However, since installing Edgy Eft and following the instructions listed in Community Help [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) , I can't get it work!  I checked all the repository boxes in Synaptic, reloaded, and entered the text that was highlighted in Terminal.  Here's the transcript of my terminal session: 

morris@morris-laptop:~$ sudo apt-get gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamers0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
Password:
E: Invalid operation gstreamer0.10-pitfdll

What am I doing wrong?  Should I remove all Bitstream apps and start over?  Help! [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by annda on 2007-03-20
you forgot one word: install. it should be:

sudo apt-get install list_of_files

also, it's a good idea to copy&paste (in the terminal: middle click or CTRL+SHIFT+v)

---

### Post by lee292 on 2007-03-20
Thank you!  I'll try again with "Install".

---

### Post by steve101101 on 2007-03-20
yes that will work. i did the same thing a while back and i use rhythmbox. just send me a message if you have any questions.

---

### Post by lee292 on 2007-03-20
It worked!  I do have another question, though.  During my terminal session, I noticed the following message:

Suggested packages:
  realplayer libdvdcss2 libdvdcss gxineplugin sidplay-base xsidplay libartsc0
Recommended packages:
  w32codecs

Should I use "sudo apt-get install" to load these packages, too?

---

### Post by annda on 2007-03-20
if you need DVD playback and RealPlayer and Windows codecs (like wma files) support, get those too.

---

### Post by lee292 on 2007-03-20
Thanks again for your help, will download and install those packages.

---

