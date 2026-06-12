---
title: "Cannot play MP3 using kaffeine Player"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by ashoka2004 on 2006-09-15
hi guys i m unable to play the mp3 files using the kafiene player also i m not able to play any video files 

tell me from where can i download a player that would help me play all sorts of files dvds/avi's/mpegs/mp3 

my kaffeine player gives the following error

there were no decoders found to handle the streamm yo might need to install the corrosponding plugins 


this is the message if i try to play mp3 thanks guys help

---

### Post by haxer on 2006-09-15
hmm.. try sudo apt-get install xmms then go to synaptic and search for streamhunter then install :)
And then search for vlc in synaptic then install :)

---

### Post by Thenotsowyzewun on 2006-09-15
For more info:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ashoka2004 on 2006-09-15
is there any other player which i can download and which can be used for playing dvd and mp3

tell me abt them as well and where can i download them from

---

### Post by Brunellus on 2006-09-15
please read the RootSudo wikipage you were linked above for information;  otherwise consider using the Automatix or EasyUbuntu setup scripts.

---

### Post by DarthSudaka on 2006-09-15
Hi
you need the codecs (yes, for mp3 too)
you can do it in, at least, two ways:
#1 is installing support, in a terminal type all of these lines (hitting ENTER after each, of course)
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

#2 (* I * recommend, its a little more complicated but also lets you easily install a lot of other useful software, like Opera, flash player, etc ) install automatix.
It´s explained here [http://ubuntuforums.org/showthread.php?t=190025]("http://ubuntuforums.org/showthread.php?t=190025")

good luck!!! :D

---

### Post by ashoka2004 on 2006-09-15
thanks guys thans a ton for ur help

---

