---
title: "Problems Downloading mplayer from WEB"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-02-18
Hi 
I am having problems down loading mplayer from the suggested web sit. 

[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

I don't see any download button.
I've gone to the repos and changed the universe to universe multiverse.

But I can't get past trying to down load mplayer.
Thanks for any help

---

### Post by jorn on 2006-02-18
Have you tried getting it by using Automatix?

- Jorn-

---

### Post by kent41 on 2006-02-18
[QUOTE=jorn]Have you tried getting it by using Automatix?

- Jorn-[/QUOTE]

Thank you for me  but I have had BAD things happen trying to use Automatix.
I have high speed connection that works very well but downloading Automatix was a disaster.

I am in the process of re-loading Ubuntu and other apps. after using Automatix.

The Automatix process is a good idea but not for me at this point

Thanks   I need to download first.

---

### Post by jorn on 2006-02-18
What do you mean "Don't see any download botton"?
Using Synaptic?
-Jorn-

---

### Post by kent41 on 2006-02-18
[QUOTE=jorn]What do you mean "Don't see any download botton"?
Using Synaptic?
-Jorn-[/QUOTE]
Jorn

I had to clean my glasses and have found the buttons.

thanks
Kent

---

### Post by patrick295767 on 2006-02-18
You can maybe try this to install most of the prg for video ...
(it's rather fast)

```
#!/bin/bash
cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home

apt-get -f -y install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs
apt-get -f -y install lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 
apt-get -f -y install gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin 
apt-get -f -y install avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin 
apt-get -f -y install avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
apt-get -f -y install gst-register-0.8

apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts flashplayer-mozilla
sudo apt-get -f -y install gstreamer0.8-plugins
sudo apt-get -f -y install gstreamer0.8-lame
sudo apt-get -f -y install gstreamer0.8-ffmpeg
sudo apt-get -f -y install w32codecs
sudo apt-get -f -y install libdivx4linux
sudo apt-get -f -y install lame
sudo apt-get -f -y install sox
sudo apt-get -f -y install ffmpeg
sudo apt-get -f -y install mjpegtools
sudo apt-get -f -y install vorbis-tools
apt-get -f -y install acroread 
apt-get -f -y install flashplayer-mozilla
apt-get -f -y install mozilla-acroread
apt-get -f -y install mplayerplug-in
apt-get -f -y install totem-xine
apt-get -f -y install mozplugger
apt-get -f -y install libflash-mozplugin
apt-get -f -y install libstdc++5
apt-get -f -y install w32codecs 
apt-get -f -y install libdvdcss2 
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer

##apt-get -f -y install totem-xine-firefox-plugin


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
  
##never forget this for all the users
echo "zoom=yes" >> ~/.mplayer/config
```


(##never forget this for all the users
echo "zoom=yes" >> ~/.mplayer/config)

Greetz

---

