---
title: "Getting RealPlayer10GOLD to work"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by one eared bat on 2005-10-31
Hi,

I have managed to download RealPlayer10, and even got it to work. However I am very new, and want to use Real Player in Firefox - but I keep getting the message "Realplayer not found in PATH. I have seen help inplaces, and each time it says "Ensure your Path ponts to realplayer. A silly question, but what is PATH, and how do I configure it?
Any help appreciated.:confused:

---

### Post by paddyg on 2005-10-31
didn't you install the realplayer plugin when asked to?

---

### Post by one eared bat on 2005-10-31
Yes, this is what I have done. Followed, as far as able, the instructions. Before I downloaded the plugin, I saw messages saying "install Real Player plugin". Now, I get the message - "could not find realplayer in the system path to use as an embedded player":confused: . So, I am further than before - just need to understand what is PATH, and how do I configure it.

---

### Post by matthewv on 2005-10-31
I think PATH is one of a number of folders that linux will look into to find a program. The easiest way to fix this is to find your realplayer installation, and the type ```
 sudo ln -s /place/where/realplayer/is/installed/realplayer /bin/realplayer 
```

Hope that works.

---

### Post by one eared bat on 2005-11-02
Thanks - I will give it a try.:D

---

### Post by homerhomer on 2005-11-12
not supported but this seems to work for me

[http://ftp.debian-unofficial.org/deb...rge.1_i386.deb](http://ftp.debian-unofficial.org/deb...rge.1_i386.deb)

*note* I didn't have video until I turned of Acceleration *

---

### Post by rajaiskandarshah on 2005-11-14
uninstall whatever it is that you have done. for example i did it from synaptic.

then please follow the following instructions from:
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483)

essentially:

1. Visit [http://www.real.com/linux/](http://www.real.com/linux/) and download Realplayer 10 for Linux into a convenient directory.

2. Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type:
 chmod +x RealPlayer10GOLD.bin

3. To install Real Player 10, run the downloaded file. Type:
 sudo ./RealPlayer10GOLD.bin

4. When prompted for a location to install RealPlayer 10, type /usr/bin/RealPlayer

5. When prompted to configure system-wide symbolic links, type "y". After that, accept the default prefix for symbolic links.

6. You can now safely remove the downloaded file from your system. Type:
 rm RealPlayer10GOLD.bin

7. To run Real Player 10, choose Applications->Sound & Video->RealPlayer 10.

---

### Post by Dafydd on 2006-04-23
[QUOTE=rajaiskandarshah]... please follow the following instructions from:
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483)[/QUOTE]

Don't think this was the original problem. 

At least for me:

How do you get Realplayer working with Firefox 1.5?

It seems a nightmare...

Dafydd

---

### Post by patrick295767 on 2006-04-23
My script for multimedia for  newbies & codecs and everthg installed at once !!! : 
(with of course,  realplayer ..)
  
greetz

```
#!/bin/bash
####################################################################################
####################################################################################
# multimedia.sh script by patrick295767 version 0.6
# april 2006 - Ubuntu Linux 
####################################################################################
#############Restoring chechkingn proper # sources.list ############################
####################################################################################
mkdir /root
mkdir /root/miniram
cd /root
cd /root/miniram
##mkdir "/home/$1/.fvwm"
echo "changing / checking the /etc/apt/sources.list (with backup)"
cd /root/miniram
rm /root/miniram/sources.list
rm /root/miniram/sources.list_extended01
wget http://patrick295767.sitesled.com/miniram/sources.list_extended01
cp "/etc/apt/sources.list" "/etc/apt/sources.list-backup"
cd /root/miniram
cp sources.list_extended01 "/etc/apt/sources.list"
apt-get update

#############" multimedia, codecs, xvidcap
## multimedia link : http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox
##
### multimedia script
mkdir /root
mkdir /root/miniram

#echo "Please enter your main user of this computer ?"
#read userpatname
#$(echo userpatname)


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
#wget http://patrick295767.sitesled.com/miniram/xmms-wma_1.0.4-2_i386.deb
cd /root/miniram
wget http://patrick295767.sitesled.com/miniram/xmms-wma_1.0.4-2_i386.deb
dpkg -i xmms-wma_1.0.4-2_i386.deb

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


cd /root/miniram
wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
### coming sitesled-codecs
cp essential-20050412.tar.bz2 essential-20050412-backup.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
 
##never forget this for all the users
echo "/home/$userpatname/.mplayer/config       to get zoom=yes in .mplayer/config"
echo "zoom=yes" >> "/home/$userpatname/.mplayer/config"




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
chmod 777 /root/xvidrec.sh
echo "xvidcap --gui no --compress 9 --file ~/myvideo.mpeg --frames 0 --fps 10 --cap_geometry 1024x768+0+0" >> "/root/xvid.sh"
echo "if you wanna make a avi file of ur screen, run sh /root/xvid.sh" 
echo "u can move this little script, where you want & need"
ln -s /root/xvidrec.sh /usr/bin/xvidrec.sh
echo "** Greetz' **"

```

---

### Post by ozPATT on 2007-01-07
realplayer10 installed nicely using the above instructions (thanks :)), but no sound... any ideas how i can get sound?

Thanks

Patrick

---

