---
title: "MPlayer doesn't work very well?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by benfinkel on 2006-04-18
Hey All,

I've downloaded the Firefox MPlayer Plugin but it doesn't seem to work very well.  About half of the pr0n err... I mean educational videos that I try to view won't play.  They just flicker for a sec and then the player says 'Stopped'

Is there a better alternative or upgraded version I'm missing?

Thanks,

-Ben

---

### Post by r4ik on 2006-04-18
Should work installed like this,

[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox)

Dont let your system get overheated.

---

### Post by Ecthelion on 2006-04-19
Hi, I have some troubles with Mplayer too..
Every time I start it up it gives an New_Face failed error.
Is there any way to make this message go away?

And sometimes when i play movies, the size of the image is very small... Is that normal too or is there anything that can be done to change that?
(don't tell me to use the option size x2, this doesn't change a thing)

---

### Post by r4ik on 2006-04-19
Try,

[http://www.ubuntuforums.org/showthread.php?t=104934&highlight=New_Face+failed](http://www.ubuntuforums.org/showthread.php?t=104934&highlight=New_Face+failed)

It IS a bit of a read but it seems to work.

Good luck !

---

### Post by patrick295767 on 2006-04-19
Hi 

There is a script for multimedia i am developping  !!
[http://patrick295767.sitesled.com/miniram/multimedia.sh](http://patrick295767.sitesled.com/miniram/multimedia.sh)

for the zoom, it's the : 
.mplayer file 
(check in the script)

Greetings !

---

### Post by r4ik on 2006-04-19
[QUOTE=patrick295767]Hi 

There is a script for multimedia i am developping  !!
[http://patrick295767.sitesled.com/miniram/multimedia.sh](http://patrick295767.sitesled.com/miniram/multimedia.sh)

for the zoom, it's the : 
.mplayer file 
(check in the script)

Greetings ![/QUOTE]

Would you be so kind to include a link to the original thread please ?
All i get now is the option to download "something"
Thanks !

---

### Post by patrick295767 on 2006-04-19
[QUOTE=r4ik]Would you be so kind to include a link to the original thread please ?
All i get now is the option to download "something"
Thanks ![/QUOTE]
  
the original thread is  there: [http://ubuntuforums.org/showthread.php?t=160070](http://ubuntuforums.org/showthread.php?t=160070)
(the download is to have the last version, for sure) 
  
 Greetings...

---

### Post by patrick295767 on 2006-04-20
Vers0.5: script multimedia :-) (I made modifications & checked it ):
```
#############" multimedia, codecs, xvidcap
## multimedia link : http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox
##
### multimedia script

echo "Please enter your main user of this computer ?"
read userpatname
#$(echo userpatname)


apt-get update
apt-get -y upgrade



## if one day, xvid and gvidcap are in repos
apt-get -f -y install xvidcap
apt-get -f -y install gvidcap
## utils apps videos player
apt-get -f -y install digikam
apt-get -f -y install audacity kaudiocreator
apt-get -f -y install mplayer-386
apt-get -f -y install digikam
apt-get -f -y install kaffeine
apt-get -f -y install guitar
apt-get -f -y install xine
apt-get -f -y install sed
apt-get -f -y install

apt-get -f -y install gnome-volume-manager
apt-get -f -y install  gxine
apt-get -f -y install audacity
## stream radio online tuner via internet
apt-get -f -y install streamripper
apt-get -f -y install streamtuner
apt-get -f -y install rhythmbox
## like realplayer
apt-get -f -y install hxplay
## stream tv online
apt-get -f -y install xawtv
apt-get -f -y install kdetv
#apt-get -f -y install xdtv
apt-get -f -y install xmltv
# camera stuffs
apt-get -f -y install camorama
## sound sound
apt-get -f -y install alsamixergui
apt-get -f -y install audacity
apt-get -f -y install ardour rezound ksim
########### tv stuffs
apt-get -f -y install xawtv
apt-get -f -y install gqcam qcam qc-usb-source qc-usb-utils
apt-get -f -y install

# Music Organizer: Cowbell
apt-get -f -y install cowbell
# ID3 Tag Editor (EasyTAG)
apt-get -f -y install easytag
# Video Editor (Kino)
apt-get -f -y install kino
apt-get -f -y install kinoplus
apt-get -f -y install kino-timfx
apt-get -f -y install kino-dvtitler
apt-get -f -y install

## juke box
apt-get -f -y install amarok
apt-get -f -y install xmms
apt-get -f -y install xmms-skins
apt-get -f -y install juk
#wget -c http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb
cd /root
wget http://patrick295767.sitesled.com/miniram/xmms-wma_1.0.4-2_i386.deb
dpkg -i /root/xmms-wma_1.0.4-2_i386.deb

cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
cp /usr/share/applications/defaults.list /tmp/defaults.list_tmp
sed -e 's/audio\/mpeg=.*/audio\/mpeg=XMMS.desktop/g' /tmp/defaults.list_tmp > /tmp/defaults.mp3
sed -e 's/audio\/x-mpegurl=.*/audio\/x-mpegurl=XMMS.desktop/g' /tmp/defaults.mp3 > /tmp/defaults.m3u
sed -e 's/audio\/x-wav=.*/audio\/x-wav=XMMS.desktop/g' /tmp/defaults.m3u > /tmp/defaults.list
mv /tmp/defaults.list /usr/share/applications/defaults.list
rm -f /tmp/defaults.*

### codecs and so on

apt-get -f -y install xine-ui
gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "xine dvd://"
rm -f /usr/share/applnk/Multimedia/xine.desktop
ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
mv /tmp/defaults.list /usr/share/applications/defaults.list


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
#gedit /etc/mplayer/mplayer.conf
#Find this line 
#vo=x11,         # To specify default video driver (see -vo help for
#Replace with the following line 
#vo=xv,         # To specify default video driver (see -vo help for
##apt-get -f -y install totem-xine-firefox-plugin


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
 
##never forget this for all the users
echo "/home/$(echo userpatname)/.mplayer/config       to get zoom=yes in .mplayer/config"
echo "zoom=yes" >> "/home/$(echo userpatname)/.mplayer/config"




######################## INSTALLATION OF PACKAGE FOLDER ##################"


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin

cd /root
##wget http://membres.lycos.fr/patrick295767/miniram/packages/realplayer10gold.bin
wget http://patrick295767.sitesled.com/miniram/real.bin
chmod 777 /root/real.bin
chmod +x /root/real.bin
./real.bin
#You could install it in /opt/Realplayer
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup


cd /usr/lib/mozilla/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup


###################### Installing xvidcap ############""
cd /root
#wget http://membres.lycos.fr/patrick295767/miniram/packages/xvidcap_1.1.3-1_i386.deb
#wget http://patrick295767.sitesled.com/miniram/xvidcap_1.1.3-p7_i386.deb
wget http://patrick295767.sitesled.com/miniram/xvidcap_1.1.3-1_i386.deb
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



```

---

### Post by _linux_ on 2006-04-21
[QUOTE=benfinkel]Hey All,

I've downloaded the Firefox MPlayer Plugin but it doesn't seem to work very well.  About half of the pr0n err... I mean educational videos that I try to view won't play.  They just flicker for a sec and then the player says 'Stopped'

Is there a better alternative or upgraded version I'm missing?

Thanks,

-Ben[/QUOTE]
Try using VLC. It plays many formats and it works. I use it and it's great!:KS

---

### Post by nalmeth on 2006-04-21
I get this happening sometimes.
Just hitting play again seems to work a lot of the time.
Just a funny bug I guess.

---

### Post by adamkane on 2006-04-21
The multimedia script installs mplayer-386. You should give the user the option to install mplayer-686 or mplayer-k7.

Any complete multimedia script should also include a recent version of ffmpeg with full ape/flac/mpc/wma/aac support:

FFMPEG v3.0.cvs-latest:
[http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb]("http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb")

(Unfortunately Issaris labels it v4.0.cvs-latest. This insures that any current version of ffmpeg will be updated to his version. This works fine until the real version 4 is released eventually.)

---

### Post by Big_J on 2006-08-19
I have found that VLC Media Player is magic, it plays almost everything including non-encrypted wmv files. Very fast and powefull, MPlayer sucks compared to it.

---

