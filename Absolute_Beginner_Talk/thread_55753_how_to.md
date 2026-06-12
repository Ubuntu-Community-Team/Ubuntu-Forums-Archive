---
title: "how to ???"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by AlMaSoUdI on 2005-08-10
after i downloaded the programs to my desktop how can i install it ?
and i can't open mp3 files the are no sound at all but when i open the vedio they are sound
i've install most of the sounds players but still can't open the mp3 files so what should i do ??

---

### Post by myha on 2005-08-10
Hi!

Im new to Linux also, but it helped me a lot reading this unoficil starter guide...:
[http://ubuntuguide.org/](http://ubuntuguide.org/)
So try finding your answer here...

Regards, miha

---

### Post by AlMaSoUdI on 2005-08-10
i've try it and read it but nothing new . the problem still on

---

### Post by xmastree on 2005-08-10
[QUOTE=AlMaSoUdI]after i downloaded the programs to my desktop how can i install it ?[/QUOTE]Why are you downloading programs to your desktop in the first place?

Unless they're programs not in the repositories, you should use symaptic or apt-get. Synaptic is better if you don't know the name of the program you need, as they're all sorted by category and you can search titles and descriptions.
You'll find it in your [COLOR=DarkSlateBlue]**System > Administration**[/COLOR] menu. Follow the ubuntu guide to add the extras.

As for your mp3s, [this](http://www.ubuntuguide.org/#codecs) is a good place to start, followed by [this](http://www.ubuntuguide.org/#xmms) 
XMMS looks just like winamp.

---

### Post by AlMaSoUdI on 2005-08-11
i already did that but still can't open mp3 songs,,,,
buy the way in thy are sound in vedio files...
even when i restart the pc thy are no sound ???

---

### Post by Jussi Kukkonen on 2005-08-11
First of all, please tell us exactly what is wrong and what your system specs are, specifically:
* what program you are trying to use
* what is the error message (if any)
* do you get any sound in Ubuntu (e.g. testing in System/Preferences/Sound)
* do you have a laptop

> buy the way in thy are sound in vedio files...
I don't know about others, but I just don't understand what you are trying to say -- I'm guessing it's something about video? Please explain your problem a little more.

---

### Post by AlMaSoUdI on 2005-08-11
[QUOTE=Jussi Kukkonen]First of all, please tell us exactly what is wrong and what your system specs are, specifically:
* what program you are trying to use
* what is the error message (if any)
* do you get any sound in Ubuntu (e.g. testing in System/Preferences/Sound)
* do you have a laptop


I don't know about others, but I just don't understand what you are trying to say -- I'm guessing it's something about video? Please explain your problem a little more.[/QUOTE]
i didn't get sound in testing and mp3 songs,but i get sound in videos.
i have audigy sound card....

---

### Post by Lord Illidan on 2005-08-11
You probably don't have mp3 codecs. Find them in the Ubuntu Guide. And it will help if you type more clearly, as your first post was extremely hard to understand. Also, don't say that there was nothing new, or otherwise you wouldn't be a beginner in the first place, and wouldn't have posted on this specific forum!

[The Ubuntu Guide](www.ubuntuguide.org)

---

### Post by KingBahamut on 2005-08-11
Illidan, Hes already stated he's tried to read the Uby Guide. 

so 

from the Uby Guide itself. 

> sudo apt-get install gstreamer0.8-plugins
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
sudo apt-get install xmms
wget -c [http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb](http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb)
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo cp /usr/share/applications/defaults.list /tmp/defaults.list_tmp
sudo sed -e 's/audio\/mpeg=.*/audio\/mpeg=XMMS.desktop/g' /tmp/defaults.list_tmp > /tmp/defaults.mp3
sudo sed -e 's/audio\/x-mpegurl=.*/audio\/x-mpegurl=XMMS.desktop/g' /tmp/defaults.mp3 > /tmp/defaults.m3u
sudo sed -e 's/audio\/x-wav=.*/audio\/x-wav=XMMS.desktop/g' /tmp/defaults.m3u > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
sudo rm -f /tmp/defaults.*


---

