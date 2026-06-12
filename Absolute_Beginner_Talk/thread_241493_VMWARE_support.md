---
title: "VMWARE support"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by gryer7421 on 2006-08-22
ok i started here:

[http://www.ubuntuforums.org/showthread.php?t=241052&highlight=mp3+question](http://www.ubuntuforums.org/showthread.php?t=241052&highlight=mp3+question)

i have reinstalled both xubuntu and ubuntu roughly 6 times now.. the box i am sitting on a home is a VM, the one here at work is a real dell gx240.

now im in the process of reinstalling the real box but my question is about the VM at home.  i got mp3 audio to *work* but it was all garbled. but the main thing was the codec seemed to play correctly.  does either xubuntu or ubuntu suport VM5?

Second part of the above, after installine mplayer and totem-xine and and vlc i cannot play dvds, this is a dvd that is NOT css encoded. it ia a wedding dvd. but mplayer and totem told me to take a hike until i get a codec... what do i need? i ask becasue i tried getting the totem plugins from plf,universe and others i have found listed in the forums but no luck at all...

**and again back to the audio issue with getting mp3/dvd support.

i am almost resinatlled back to a fresh copy of xubuntu on the dell gx240.  what exact libareies do i need?  i aks this becasue it seems the installers just dont have what i need, not even from PLF...

---

### Post by gryer7421 on 2006-08-22
i just grabbed my install list.. heres what i am installing from root command line..

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly 
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
sudo apt-get install w32codecs
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
sudo apt-get install totem-xine
sudo apt-get install xine-ui libxine-extracodecs
gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "xine dvd://"
sudo rm -f /usr/share/applnk/Multimedia/xine.desktop
sudo ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
sudo apt-get install vlc vlc-plugin-* mozilla-plugin-vlc
sudo apt-get install totem-gstreamer-firefox-plugin
sudo apt-get install xmms
sudo apt-get install xmms-skins
wget -c [http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb](http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb)
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo cp /usr/share/applications/defaults.list /tmp/defaults.list_tmp
sudo sed -e 's/audio\/mpeg=.*/audio\/mpeg=XMMS.desktop/g' /tmp/defaults.list_tmp > /tmp/defaults.mp3
sudo sed -e 's/audio\/x-mpegurl=.*/audio\/x-mpegurl=XMMS.desktop/g' /tmp/defaults.mp3 > /tmp/defaults.m3u
sudo sed -e 's/audio\/x-wav=.*/audio\/x-wav=XMMS.desktop/g' /tmp/defaults.m3u > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
sudo rm -f /tmp/defaults.*
sudo apt-get install amarok
sudo apt-get install kino
sudo apt-get install kinoplus
sudo apt-get install kino-timfx
sudo apt-get install kino-dvtitler
sudo apt-get install audacity
sudo apt-get install banshee
sudo apt-get install dvdrip vcdimager cdrdao subtitleripper
sudo ln -fs /usr/bin/rar /usr/bin/rar-2.80
gksudo gedit /usr/share/applications/dvdrip.desktop

and this is my source. <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) dapper free non-free
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by gryer7421 on 2006-08-22
bump*

---

### Post by gryer7421 on 2006-08-22
bump*

---

### Post by gryer7421 on 2006-08-22
bump issue was the mp3's, it appears that all of mp3.com is using somthing that the codecs dont like... after decoding back to a wav and then back to lame... they all play now.

odd

---

