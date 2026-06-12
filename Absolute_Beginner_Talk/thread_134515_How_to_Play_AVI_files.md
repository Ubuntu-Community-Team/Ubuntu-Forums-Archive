---
title: "How to Play AVI files"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by FinePix on 2006-02-22
Can some one help me to play avi movie clips in ubuntu . i cannot play avi files in Totem Movie Player.

---

### Post by Perfect Storm on 2006-02-22
enable universe in the sourcelist. Also add multiverse and PLF.

```
sudo gedit /etc/apt/sources.list
```

Uncomment the lines where there's a #

add:

[b]## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```
sudo apt-get update
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
gst-register-0.8

```

But you might try mplayer or vlc as they are better to the job.


You can also try Automatix, check my sig.

---

### Post by masingerz on 2006-02-23
Dear Forum:

I tried the previously mentioned commands and:

I get (notice the word "abort" in the end:
carlos@masingerz:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://eros.vlo.gda.pl](http://eros.vlo.gda.pl) ./ Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://eros.vlo.gda.pl](http://eros.vlo.gda.pl) ./ Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://eros.vlo.gda.pl](http://eros.vlo.gda.pl) ./ Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://eros.vlo.gda.pl](http://eros.vlo.gda.pl) ./ Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Fetched 4B in 3s (1B/s)
Reading package lists... Done
carlos@masingerz:~$ sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-plugins is already the newest version.
gstreamer0.8-ffmpeg is already the newest version.
w32codecs is already the newest version.
sox is already the newest version.
libdvdcss2 is already the newest version.
libdvdnav4 is already the newest version.
libdvdread3 is already the newest version.
The following extra packages will be installed:
  gstreamer0.8-dirac gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-wavpack
  gstreamer0.8-xvid libavifile-0.7 libdc1394-13 libdirac0 libfaac0 libfaad2-0
  libimlib2 liblame0 libmjpegtools0 libmp4v2-0 liboggflac3 libwavpack0
  libxvidcore4
Suggested packages:
  avifile-player avifile-utils toolame mpeg2dec a52dec
The following NEW packages will be installed:
  avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin
  avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin ffmpeg
  gstreamer0.8-dirac gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-lame
  gstreamer0.8-plugins-multiverse gstreamer0.8-wavpack gstreamer0.8-xvid lame
  libavifile-0.7 libdc1394-13 libdirac0 libdvdplay0 libfaac0 libfaad2-0
  libimlib2 liblame0 libmjpegtools0 libmp4v2-0 liboggflac3 libwavpack0
  libxvidcore4 mjpegtools vorbis-tools
0 upgraded, 30 newly installed, 0 to remove and 0 not upgraded.
Need to get 8533kB of archives.
After unpacking 23.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
carlos@masingerz:~$

---

### Post by Madpilot on 2006-02-23
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) will take you through installing all the codecs you'll need, without doing messy stuff like adding extra repos or using Automatix.

---

### Post by bgoody on 2006-02-23
[QUOTE=masingerz]Dear Forum:

I tried the previously mentioned commands and:

I get (notice the word "abort" in the end:

Do you want to continue [Y/n]? y
Abort.

Hi.  If you don't enter a CAPITAL Y, it thinks you entered n and therefore aborts.
Brian

---

### Post by drewbie on 2006-02-23
[QUOTE=bgoody][QUOTE=masingerz]

Hi.  If you don't enter a CAPITAL Y, it thinks you entered n and therefore aborts.
Brian[/QUOTE]

I always thought that the captial letter showed the defalt option, pressing just <enter> or Y or y should be enough.

are you sure you have enough disk space?

---

### Post by frodon on 2006-02-23
[QUOTE=Madpilot]without doing messy stuff like adding extra repos or using Automatix.[/QUOTE]It's a point of view.

---

### Post by masingerz on 2006-02-23
I tried capital Y and same problem, and yes I do have disc space theres like 64 Giga left on the disc

---

### Post by Perfect Storm on 2006-02-23
Try install them seperatly, or in smaller part, that might work.

---

### Post by kvorion on 2006-02-23
You could install vlc. IMO its the best player to play avi files on any linux (thats a personal choice). You can apt-get it or else use automatix to install it.

---

### Post by DiscoKiller on 2006-02-23
Just a little extra to this thread. I had a problem with playing AVI files and the like a while ago, my solution was to install the latest vVidia drivers (doii!!) which did the trick. Just in case you havent thought of that....not likely though, im pretty sure i`m the only proper dumbass who doesnt install drivers for his hardware :)


DK

---

### Post by masingerz on 2006-02-23
Dear Forum:

I tried pasting the commands in 3 groups as it was sugggested before:

I dont get "abort" anymore,  but... still totem only plays -some- avi files
it does not play all avi files...


sudo apt-get update
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg 

sudo apt-get install mjpegtools vorbis-tools libdvdcss2 gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin 

sudo apt-get install avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
gst-register-0.8

---

### Post by Perfect Storm on 2006-02-24
Try with VLC then. I run all my .avi files with that.

---

### Post by ezphilosophy on 2006-02-24
[QUOTE=Madpilot][https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) will take you through installing all the codecs you'll need, without doing messy stuff like adding extra repos or using Automatix.[/QUOTE]

I wouldn't think that you could put "messy" and "Automatix" together.  Automatix is a fantastically easy way (and not "messy") to get your system set-up, especially for beginners.  I would think that even for advanced users, clicking a couple of buttons, walking away from your computer for awhile and coming back to a basically set-up system is a bit more convenient that hacking away at the keyboard for a couple of hours.

So, basically, in agreement with A.I., Automatix would be a good way to get those .avi files (and others) playing.

---

### Post by patrick295767 on 2006-02-24
You can maybe try this script to install most of the prg for video ...
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


Greetz

---

### Post by minhaaj on 2008-07-19
even vlc won't play my youtube downloaded avi files. i am pretty much sick of installing everything like gstreamer, restricted formats etc. i have tried everything but it isn't working.

---

