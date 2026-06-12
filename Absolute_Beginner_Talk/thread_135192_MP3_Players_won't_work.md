---
title: "MP3 Players won't work"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by Piney Woods on 2006-02-23
I can't get any sound from the mp3 players that come with Ubuntu.  I have amarok, juk, xmms, kaffiene etc....none will play.  I have made sure to get the correct engines downloaded from the repositories but each time I try to play an mp3...nothing happens.  I can load the mp3 fine, no problem...it just won't play.  I also wanted to be able to listen to podcasts through amarok...and nothing.

Oh and by the way, my sound card is working fine.  Just can't play mp3's. 
Any ideas would be appreciated.

PW

System Specs:
Ubuntu 5.10 (Breezy Badger)
AMD Duron 1.0 Ghz
20 GB Maxtor HD.
ECS K7S5A with onboard sound
192 MB DDR Ram

---

### Post by Brunellus on 2006-02-23
please visit the RestrictedFormats wikipage, or, alternatively, search for Automatix on these forums.

---

### Post by ajgreeny on 2006-02-23
you need the mp3 codecs to be able to play them.  Use synaptic to install lame, liblame0,  gstreamer0.8mad and gstreamer0.8-lame and you may find all is working.

---

### Post by Sutekh on 2006-02-23
[QUOTE=Brunellus]please visit the RestrictedFormats wikipage, or, alternatively, search for Automatix on these forums.[/QUOTE]
[Ubuntu Wiki - Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats")

 - because searching the wiki isn't easy

---

### Post by Piney Woods on 2006-02-24
Thanks for the information.  I can now hear my mp3's.

I installed Automatix and WOW!! what a great resource.  I don't think it upgraded my Firefox or Thunderbrid however.  It still shows that I have versions 1.0.7.  I understood it would upgrade both to the newest versions.  Does anyone know how frequently the repositories are updated? They seem rather slow to me.

Thanks again,
PW

---

### Post by arnieboy on 2006-02-24
run automatix again to upgrade your firefox and thunderbird.

---

### Post by patrick295767 on 2006-02-24
To Help the Videos, to work better

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


 Easy and rather fast to be done & installed
(check the ##never forget this for all the users)

------------
dwl from the website: [http://www.real.com/linux?pcode=rn&opage=freeplayer_partner&src=freepl](http://www.real.com/linux?pcode=rn&opage=freeplayer_partner&src=freepl) ayer_partner
(to install realplayer:
chmod +x realplay.bin
./realplay.bin
& correct mv... and so on ...

---

### Post by Piney Woods on 2006-02-24
Running Automatix again worked. The first time it ran, I thought it downloaded the new versions but apparently not.  This time, I selected both and now I have  the newest versions.  Thanks for pointing me to Automatix.  It's a great resource when installing programs into linux.

PW

---

