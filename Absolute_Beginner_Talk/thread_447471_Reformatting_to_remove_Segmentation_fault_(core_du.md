---
title: "Reformatting to remove Segmentation fault (core dumped) - Help."
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Carwyn on 2007-05-18
My Ubuntu is completely messed up, keep getting "Segmentation fault (core dumped)" from any "sudo apt" command.

So I need to reformat, but I have a lot of important media in my '/home' directory that I don't want to lose and have no means to back it up (all my back up drives and externals are full as well). So are there any things I need to make sure the error won't come back after reinstalling Ubuntu? Mainly any files that would need to be manually deleted from '/home'

---

### Post by hardyn on 2007-05-18
segmentation faults are about memory... 

a reinstall should take care of any problems that are related to corrupt files.  im not sure why you would be getting those errors with apt-get... what did you do before this started to happen?

---

### Post by Carwyn on 2007-05-18
```
carwyn@Yuri:~$ sudo pon dsl-providerPassword:Plugin rp-pppoe.so loaded.carwyn@Yuri:~$ sudo gedit /etc/X11/xorg.conf
carwyn@Yuri:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
OK
carwyn@Yuri:~$ sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
--00:11:29--  http://medibuntu.sos-sts.com/sources.list.d/feisty.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving medibuntu.sos-sts.com... 81.169.138.125, 88.191.13.100, 88.191.26.58, ...
Connecting to medibuntu.sos-sts.com|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 240 [text/plain]

100%[====================================>] 240           --.--K/s             

00:11:30 (18.78 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [240/240]
carwyn@Yuri:~$ sudo apt-get update
Get:1 http://cn.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://cn.archive.ubuntu.com feisty/main Translation-en_US  

[lots of packet information]

Reading package lists... Done
carwyn@Yuri:~$ sudo aptitude install w32codecs
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install w32codecs
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install libxine-extracodecs xine-ui mplayer mplayer-skins vlc vlc-plugin-*
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install xmms xmms-mad xmms-skins xmms-wma mpg123 banshee amarok
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install libxine-extracodecs xine-ui
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install flashplugin-nonfree
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude
Segmentation fault (core dumped)

```

Which is why I think when I reformatted something important wasn't deleted.

---

