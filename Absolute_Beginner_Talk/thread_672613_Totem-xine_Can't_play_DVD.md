---
title: "Totem-xine Can't play DVD"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by glenna on 2008-01-19
I've been trying to get Totem-xine to work on my TravelMate 6292.  I found this on the forum:

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

I did this.  Now when I put a dvd in, this is the error message I get:

The source seems encrypted and cannot be read.  Are you trying to play encrypted dvd without using libdvdcss?

I looked and I have libdvdcss2.

Any thoughts?

Glenn

---

### Post by glenna on 2008-01-19
I just found a message that libdvdcss2 was broken, so I removed it.  I will wait to hear before I try to install it again.

Glenn

---

### Post by jleaker01z on 2008-01-19
Check Applications>Add/Remove to see if you have the DVD codecs installed.  In fact, you could just search for 'codec' and then install anything that says it provides said codecs.  (Mp3s, wavs, dvds etc).  I believe they are called 'plugins' and should be for 'gstreamer'.

---

### Post by mc4man on 2008-01-19
get the latest libdvdcss2 here [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/) 
(you don't need the dev )
i've read but don't know from experience that having this installed is useful with xine
libxine1-ffmpeg

---

### Post by glenna on 2008-01-19
More problems.  

First I tried downloading the libdvdcss2 from the website and got this error message:

Error: wrong architecture (i386)

Second:  I tried to install xine extra plugins and got this error message:

xine extra plugins can not be installed on your computer type (amd64).  either the application requires special features the vendor does not support your computer type,

Lots of problems......

Glenn

---

### Post by RomeReactor on 2008-01-19
Hi. It seems you have Ubuntu 64-bit; try this from the terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
To add the [Medibuntu]("http://medibuntu.org/") repositories; then:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
To get the GPG key and update the repository information on the package managers; and:
```
sudo aptitude install libdvdread3 libdvdnav4 libdvdplay0 libdvdcss2 libxine1-ffmpeg libxine1-gnome libxine1-plugins w64codecs
```

---

### Post by glenna on 2008-01-19
Tried it...still nothing.  Maybe this is a dumb question:  Did I download the wrong Ubuntu?  I have an Acer TravelMate 6292.......
[http://us.acer.com/public/page4.do?link=oln56.redirect&dau22.oid=24419&UserCtxParam=0&GroupCtxParam=0&dctx1=25&CountryISOCtxParam=US&LanguageISOCtxParam=en&ctx3=-1&ctx4=United+States&crc=2278501570](http://us.acer.com/public/page4.do?link=oln56.redirect&dau22.oid=24419&UserCtxParam=0&GroupCtxParam=0&dctx1=25&CountryISOCtxParam=US&LanguageISOCtxParam=en&ctx3=-1&ctx4=United+States&crc=2278501570)

---

### Post by RomeReactor on 2008-01-19
Ubuntu 64-bit is very well supported nowadays; regarding DVD playback it makes practically no difference whether you have 32-bit or 64. Are you sure you have Totem-Xine installed? please post the output of:
```
aptitude search totem
```

---

### Post by glenna on 2008-01-19
Here it is:

p   libtotem-plparser-dev           - Totem Playlist Parser library - developmen
i   libtotem-plparser7              - Totem Playlist Parser library - runtime ve
i   totem                           - A simple media player for the Gnome deskto
c   totem-gstreamer                 - A simple media player for the Gnome deskto
v   totem-gstreamer-firefox-plugin  -                                           
i   totem-mozilla                   - Totem Mozilla plugin                      
i   totem-xine                      - A simple media player for the Gnome deskto
v   totem-xine-firefox-plugin

---

### Post by RomeReactor on 2008-01-19
Try switching back to Totem-Gstreamer:
```
sudo aptitude install totem-gstreamer ubuntu-restricted-extras
```

---

### Post by glenna on 2008-01-19
OK...back to totem g-streamer.  Now it says I need appropriate plugins??  

I sure do appreciate the help!!!  I hope you don't mind that I step by step.  I've played with for so long, I've probably caused as many problems.

Glenn

---

### Post by RomeReactor on 2008-01-20
Did the packages install correctly? Let's make sure you have everything installed:
```
sudo aptitude install totem-gstreamer gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4
```
And post the output.

---

### Post by glenna on 2008-01-20
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "libdvdplay0"
The following NEW packages will be installed:
  gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 108kB of archives. After unpacking 401kB will be used.
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe gstreamer0.10-fluendo-mp3 0.10.5.debian-1 [51.2kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe gstreamer0.10-fluendo-mpegdemux 0.10.12-0ubuntu1 [56.9kB]
Fetched 108kB in 2s (39.8kB/s)                     
Selecting previously deselected package gstreamer0.10-fluendo-mp3.
(Reading database ... 99692 files and directories currently installed.)
Unpacking gstreamer0.10-fluendo-mp3 (from .../gstreamer0.10-fluendo-mp3_0.10.5.debian-1_amd64.deb) ...
Selecting previously deselected package gstreamer0.10-fluendo-mpegdemux.
Unpacking gstreamer0.10-fluendo-mpegdemux (from .../gstreamer0.10-fluendo-mpegdemux_0.10.12-0ubuntu1_amd64.deb) ...
Setting up gstreamer0.10-fluendo-mp3 (0.10.5.debian-1) ...
Setting up gstreamer0.10-fluendo-mpegdemux (0.10.12-0ubuntu1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

---

### Post by RomeReactor on 2008-01-20
I forgot that libdvdlpay0 is no longer in the Ubuntu repositories; in its place. libdvdnav4 is used. Does this problem happen with all other DVDs? have you set the region code on your DVD drive? to check, run:
```
hdparm /dev/dvd
```
Preferably, it should not be set. If it is, maybe it's the wrong region.

---

### Post by glenna on 2008-01-20
So far it has been all DVD's.  I just tried a few more....no luck.  I've never even used a DVD in this computer when using XP...I'll try it.

/dev/dvd:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

I don't know if this is good or bad.

---

### Post by glenna on 2008-01-20
DVD player works -- not a hardware issue.

g

---

### Post by glenna on 2008-01-20
Finally got things working with the following code:

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse libdvdcss2

I did have to upgrade to xine.  Totem-xine plays most dvd's, not all.  BUT VLC does play every DVD i've tried so far.

Thanks for everybodies help.

Glenn

---

### Post by jposton on 2008-02-23
Wow, I finally got my computer to play a DVD. 

:popcorn:

---

### Post by martin saint martin on 2008-03-20
i´m having the same problem with dvds tried the  sudo aptitude install totem-gstreamer ubuntu-restricted-extras
 and this is what i got

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what does this mean?

---

### Post by sbassett on 2008-05-06
> **martin saint martin said:**
> i´m having the same problem with dvds tried the  sudo aptitude install totem-gstreamer ubuntu-restricted-extras
 and this is what i got

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what does this mean?

Make sure Synaptic or the Updater is not running when you execute this.

---

