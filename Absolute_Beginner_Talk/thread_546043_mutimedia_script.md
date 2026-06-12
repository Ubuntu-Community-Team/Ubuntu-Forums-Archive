---
title: "mutimedia script"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by prophet73 on 2007-09-08
Hi im trying to create a multimedia install script for my farther to use but im a newb myself and not 100% if this is going to work.Can anyone tell me how to improve on this or let me know if there is any problems with it please.
#!/bin/bash

#Enable all repos
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
sudo apt-get update

#Add extra repos for multimedia codecs/apps
echo "deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0" | sudo tee -a /etc/apt/sources.list
echo " deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0" | sudo tee -a /etc/apt/sources.list
echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
#install codecs/apps

sudo apt-get -y install ubuntu-restricted-extras
sudo apt-get -y install w32codecs
sudo apt-get -y install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
sudo apt-get -y install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get -y install totem-xine
sudo apt-get install libdvdcss2
sudo apt-get -y install mozilla-mplayer
sudo apt-get -y install helix-player mozilla-helix-player
sudo apt-get -y install amarok
sudo apt-get -y install vlc vlc-plugin-*
sudo apt-get -y install mozilla-plugin-vlc
wget [http://download.deluge-torrent.org/ubuntu/feisty/0.5.3/deluge-torrent_0.5.3-1_i386.deb](http://download.deluge-torrent.org/ubuntu/feisty/0.5.3/deluge-torrent_0.5.3-1_i386.deb) && \
sudo apt-get -y install libboost-date-time1.33.1 libboost-filesystem1.33.1 libboost-thread1.33.1 && \
sudo dpkg -i deluge-torrent_0.5.3-1_i386.deb && \
rm  deluge-torrent_0.5.3-1_i386.deb
sudo apt-get -y install k3b 
sudo apt-get -y install libk3b2-mp3
sudo apt-get -y install gtk-gnutella

#Copy icons to desktop
cp '/usr/share/applications/kde/amarok.desktop' '/home/theclarks/Desktop' 
cp '/usr/share/applications/vlc.desktop' '/home/theclarks/Desktop'
cp '/usr/share/applications/kde/k3b.desktop' '/home/theclarks/Desktop'
cp '/usr/share/applications/hxplay.desktop' '/home/theclarks/Desktop'  
cp '/usr/share/applications/firefox.desktop' '/home/theclarks/Desktop'

---

### Post by prophet73 on 2007-09-09
Well it all worked apart from deluge here's the updated version if anyone wants to use it.
#!/bin/bash



#Enable all repos

sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig

sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list

sudo apt-get update



#Add extra repos for multimedia codecs/apps

echo "deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0" | sudo tee -a /etc/apt/sources.list

echo " deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0" | sudo tee -a /etc/apt/sources.list

echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list

wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update



#install codecs/apps

sudo apt-get -y install ubuntu-restricted-extras

sudo apt-get -y install w32codecs

sudo apt-get -y install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

sudo apt-get -y install libdvdread3

sudo /usr/share/doc/libdvdread3/install-css.sh

sudo apt-get -y install totem-xine

sudo apt-get install libdvdcss2

sudo apt-get -y install mozilla-mplayer

sudo apt-get -y install helix-player mozilla-helix-player

sudo apt-get -y install amarok

sudo apt-get -y install vlc vlc-plugin-*

sudo apt-get -y install mozilla-plugin-vlc

sudo apt-get -y install k3b

sudo apt-get -y install libk3b2-mp3

sudo apt-get -y install gtk-gnutella

---

