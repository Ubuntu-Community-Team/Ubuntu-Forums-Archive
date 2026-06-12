---
title: "totem player problem"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by md isa on 2006-01-29
Hello friends out there,
I'm totally new to Ubuntu.  Ubuntu was installed as my OS by a friend and suggest me to used it.  It,s nice but I have a problem with totem player.  When I tried to play video from internet, it appeares " totem could not play 'fd//0'.
Can anyone :???: out there tell me what is that all about and how to overcome that problem.

---

### Post by Perfect Storm on 2006-01-29
[http://ubuntuforums.org/showthread.php?t=104958](http://ubuntuforums.org/showthread.php?t=104958) check last post. You might also search the forums for enable universe multiverse and PLF to the sourcelist.

---

### Post by Kimm on 2006-01-29
Totem can be a pain sometimes, but there are some workarounds for it.

I suggest changing to totem-xine (the one installed is probably totem-gstreamer), to do that just type:

sudo apt-get install totem-xine

in your terminal and it will be taken care of. Another thing that you can do is change player all together, by installing something like VLC or Gxine, I recommend gxine, to do that, just type

sudo apt-get install gxine

(that wount hurt totem)

---

### Post by patrick295767 on 2006-01-29
I am using this to make everthg working... 

Greetz
  
```
cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home
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

### Post by md isa on 2006-01-30
Thanks to the advice given.
Even though the problems are not all fix, but I managed to get to play a few movie right now.:)

---

### Post by Perfect Storm on 2006-01-31
You may try another media-player like mplayer or VLC.

---

