---
title: "SOLVED Dummy output"
date: 2013-03-26
forum: Any Other OS
---

### Post by Exil on 2013-03-26
I did a really really stupid thing 

I have been struggling with my USB Sennheiser PC 36 CALL CONTROL headset for a while trying to get the recording sound in Audacity up to a decent level but without much luck.

So today I once get search for solutions when I came a cross a thread that suggested to try something in another thread and even though the thread was from 2010 I went ahead and did it. And now I am without sound :(

This is the thread: [http://ubuntuforums.org/showthread.php?t=1395089](http://ubuntuforums.org/showthread.php?t=1395089) and I copied the whole long thing into terminal and ran it.
Can somebody help me undo whatever it is the command did, and perhaps even get a decent sound recording volume?

I'll just go and bang my head into the wall for a while

Thank you :)

---

### Post by Exil on 2013-03-27
This is the command I was stupid enough to run:

sudo aptitude install libdns53 libdns53 ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-20-generic linux-backports-modules-alsa-2.6.31-20-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-headers-lbm-2.6.31-20-generic vlc

Also I do not have a dedicated sound card. I use the sound provided with my ASUS 1155 P8H61-M PRO REV 3.0 motherboard.

---

### Post by Impavidus on 2013-03-27
That command tried to install 131 different packages, many of which have nothing to do with sound (data compression, fonts), many of which were allready installed on your machine (probably), many of which never have to be installed manually as they are automatically included by others and some of which are no longer available as they were specific to an older Ubuntu version (karmic koala, which is 9.10 and dead for two years now).

Can you tell us which Ubuntu version you are running?

---

### Post by schragge on 2013-03-27
That command calls [aptitude](http://manpages.ubuntu.com/manpages/precise/en/man8/aptitude.8.html), but do you have *aptitude* installed at all? IIRC, it's not part of default installation on recent Ubuntu releases anymore. Could you please post the output of ```
dpkg -l aptitude
```

---

### Post by Exil on 2013-03-27
Hi,

I am actually on Linux Mint Nadia, which if I am not mistaken is built on Ubuntu 12:10

Output of dpkg -l aptitude

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  aptitude       0.6.8.1-2ubu amd64        terminal-based package manager


Thanks

---

### Post by schragge on 2013-03-27
Could you please publish the aptitude and dpkg logs using pastebin and post the links here?

aptitude:
```

sudo apt-get install pastebinit
pastebinit /var/log/aptitude

``` Then post the link.

dpkg:
```

grep ^2013-03-27 /var/log/dpkg.log|pastebinit

``` Likewise post the link.

---

### Post by Exil on 2013-03-27
This is my output:

 ~ $ pastebinit /var/log/aptitude
You are trying to send an empty document, exiting.

 ~ $ grep ^2013-03-27 /var/log/dpkg.log|pastebinit
[http://pastebin.com/h2ednx4B](http://pastebin.com/h2ednx4B)

thanks

---

### Post by Exil on 2013-03-27
is this normal?

sudo aplay -l
aplay: device_list:252: no soundcards found...

---

### Post by Perfect Storm on 2013-03-27
Moved to Other OS/Distro Talk.

---

### Post by Exil on 2013-03-27
Finally solved by running:

> sudo modprobe snd-hda-intel

---

