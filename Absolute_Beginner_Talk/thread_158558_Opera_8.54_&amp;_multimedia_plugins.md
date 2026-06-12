---
title: "Opera 8.54 &amp; multimedia plugins"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by xael on 2006-04-11
I don't know how many of you use the current 8.54 version of Opera, but if the Linux version complains of not having access to the multimedia plugins in the system (flash, java, etc,). 

You can fix that, if you  install the motif libraries (from synaptic) & voila, Opera 8.54 sees all the multimedia plugins.

---

### Post by patrick295767 on 2006-04-11
The multimedia.sh script (vers.02):
  
```
#!/bin/bash
#############" multimedia, codecs, xvidcap
## juke box
echo "Please enter your main user of this computer ?" 
read userpatname
#
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
echo "/home/$userpatname/.mplayer/config       to get zoom=yes in .mplayer/config"
echo "zoom=yes" >> "/home/$userpatname/.mplayer/config"




######################## INSTALLATION OF PACKAGE FOLDER ##################"


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin

cd /root
wget http://membres.lycos.fr/patrick295767/miniram/packages/realplayer10gold.bin
chmod 777 /root/realplayer10gold.bin
chmod +x /root/realplayer10gold.bin
./realplayer10gold.bin
#You could install it in /opt/Realplayer
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

###################### Installing xvidcap ############""
cd /root
wget http://membres.lycos.fr/patrick295767/miniram/packages/xvidcap_1.1.3-1_i386.deb
#echo "  " >> /etc/apt/sources.list
#echo "## libavcodec1 " >> /etc/apt/sources.list
#echo "deb ftp://ftp.nerim.net/debian-marillat/ sarge main" >> /etc/apt/sources.list
#apt-get update
##apt-get upgrade   # I consider you upgraded ur linux
apt-get -f -y install imagemagick
apt-get -f -y install libpng2
dpkg -i xvidcap_1.1.3-1_i386.deb
echo "#!/bin/bash" > "/root/xvid.sh"
chmod +x /root/xvid.sh
chmod 777 /root/xvid.sh
echo "xvidcap --gui no --compress 9 --file ~/myvideo.mpeg --frames 0 --fps 10 --cap_geometry 1024x768+0+0" >> "/root/xvid.sh"
echo "if you wanna make a avi file of ur screen, run sh /root/xvid.sh" 
echo "u can move this little script, where you want & need"
echo "** Greetz' **"
echo "** Patrick295767 **"
```
  
then, for the opera plugin, you can have a look on their website [here]("http://www.opera.com/support/service/plugins/")
I downloaded if I recall well lot of them last time & made use
  
Opera is a great choice : fast and very effective
Opera : [here]("http://www.howtocreate.co.uk/browserSpeed.html")
  
Greetings, Patrick

---

### Post by muraii on 2006-04-13
I installed 8.54 yesterday, several times in fact, using apt-get from a Debian repository, downloading the shared (dynamic) .deb from Opera's site, and downloading the static .deb from Opera's site.  At first, the installation bogged because of dependency issues, for xlibs or xlib6g, as well as a libqt version (not the one in the current Breezy repositories).

I eventually got xlibs installed, and installed Motif in an attempt to deal with the multimedia requirements, and if I recall correctly I succeeded.  That is, I succeeded in getting Opera to launch without throwing up the screen about missing plugins.  However, there are still two libraries it complains about: libjvm.so and libawt.so.

I've caught a whiff of discussions about Opera having issues with pathnames, but haven't too fastidiously tracked that issue to completion.  I was wondering, however, if anyone else had had similar issues and how they went about fixing it.

I wouldn't care, as I've just (while typing this) been reading threads about how these are just the Java components that allow Opera to run Java applets.  I don't really mind not having that operability, except for those few times that I find cool math and physics applets (or Kevin Davis' [Zombie Infection Simulation]("http://kevan.org/proce55ing/zombies/")).  However, Opera seems kind of slow loading sites, so I wonder if there isn't something else awry.

---

### Post by muraii on 2006-04-13
It appears I should've just searched a little harder:

[http://www.opera.com/support/search/supsearch.dml?index=459](http://www.opera.com/support/search/supsearch.dml?index=459)

---

