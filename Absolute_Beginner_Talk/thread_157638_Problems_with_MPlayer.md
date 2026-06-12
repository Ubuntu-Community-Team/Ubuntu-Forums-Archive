---
title: "Problems with M/Player"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-04-09
I am new to Ubuntu. I am having problems viewing video clips from the internet using Mozilla Fireofx. For instance, the moment I click on any video clip from BBC, a MPlayer window opens up (embedded video etc.); after a few second it stops. And thats it. I can view nothing. 

Why doesn't the RealPlayer10 window open up?

---

### Post by halitech on 2006-04-09
Do you have RealPlayer installed and what version of FF do you have?

---

### Post by aktiwers on 2006-04-09
Hi,

I have used this extension to firefox to fix this problem:
[http://membres.lycos.fr/sethnakht/](http://membres.lycos.fr/sethnakht/)

I know there is a real way to do it, but dont know how. This extension lets you pick wich player to use when.

---

### Post by patrick295767 on 2006-04-09
my script :


```
#!/bin/bash
#############" multimedia
## juke box
apt-get -f -y install xmms
apt-get -f -y install juk


### codecs and so on
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




######################## INSTALLATION OF PACKAGE FOLDER ##################"


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin
chmod 777 /root/RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin       #You could install it in /opt/Realplayer
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

cd /usr/lib/mozilla/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup
```

---

### Post by aam-aadmi on 2006-04-10
Sorry about the delay in replying...was out of town for a day.  

I have RealPlayer 10 installed and I am running Firefox 1.5.0.1.

But I cannot watch video clips from the internet...problem with M/Player. Why doesn't Real Player become the default? Can I make it the default somehow? Or is there some other way to fix the problem of M/Player?

---

### Post by rvergara on 2006-04-10
I have exactly the same problem.

I also have FF 1.5.0.1 and RP 10. I installed both with Automatix.

Can I make RP10 my default video player for FF?

Regards

Ramiro

---

### Post by aam-aadmi on 2006-04-10
Is it possible that there is some problem with the Automatix script? Because I had also installed Real Player using Automatix?

Can someone help?

---

### Post by KansasJoe on 2006-04-11
You can set a default program to run your videos by going to the mozilla toolbar on top and then

Tools
Extensions
Get More Extensions

Then look for mediaplayer connectivity (something like that) and with this you can pick what media player will be used by default for certain types of videos and such

---

