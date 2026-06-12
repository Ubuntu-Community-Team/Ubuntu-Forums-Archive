---
title: "W32 codec installation pblm"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by Maccabee on 2006-01-14
I want to install W32 codecs on a system without net connection.I downloaded the file and tried to install using dpkg -i but got the following error.
> 
Unpacking w32codecs (from w32codecs_20050412-0.0_i386.deb) ... dpkg-deb: subprocess paste killed by signal (Broken pipe) dpkg: error processing w32codecs_20050412-0.0_i386.deb (--install): short read in buffer_copy (backend dpkg-deb during `./usr/lib/win32/drv3.so.6.0') Errors were encountered while processing: w32codecs_20050412-0.0_i386.deb 


Can any one provide a solution

---

### Post by ubuntu_demon on 2006-01-14
IMHO the best way is to use the plf repository and install(and update) w32codecs from there. For information how to do that see here :

[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

But most people also want other repositories such as backports. So see my signature for my sources.list and some information on it.

---

### Post by patrick295767 on 2006-01-14
I used this (but pitty u dont have any internet)

```
cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home
apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts
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
apt-get -f -y install w32codecs 
apt-get -f -y install libdvdcss2 
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin
chmod 777 /root/RealPlayer10GOLD.bin
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

