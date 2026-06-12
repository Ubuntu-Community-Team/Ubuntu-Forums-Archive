---
title: "Playing DVDs"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Foustus on 2006-11-14
Having trouble playing DVDs. When I insert a DVD into the drive, Totem comes up and says that I need the proper plugins but it doesn't say what those are. Can someone help. Thanks. I am running Ubuntu 6.10

---

### Post by aidanr on 2006-11-14
install [automatix]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29") and using automatix install AUD-DVD Codecs

---

### Post by Cariboo1938 on 2006-11-14
> **Foustus said:**
> Having trouble playing DVDs. When I insert a DVD into the drive, Totem comes up and says that I need the proper plugins but it doesn't say what those are. Can someone help. Thanks. I am running Ubuntu 6.10That's what I did:> DVD Player for Ubunu 6.10 "Edgy Eft"

For Copyright reasons, Ubuntu does not come with a DVD player to play commercial, encrypted DVDs.
To enable play-back of commecrial/encrypted DVDs follow these instructions:


1) Install Totem-Xine Mplayer

-->Open "Terminal" (and use Command line)
   -->Type command: "sudo apt-get install totem-xine mplayer"

The following packages were automatically installed and are no longer required:
  totem-gstreamer
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libartsc0 libdvdread3 libfaac0 libggi2 libgii1 libgii1-target-x liblame0
  libmodplug0c2 libmp4v2-0 libmpcdec3 libungif4g libxine1 libxvidcore4
  libxvmc1 mplayer-skins
Suggested packages:
  libdvdcss2 libggi-target-emu libggi-target-monotext libggimisc2 w32codecs
  libdvdcss mplayer-doc
Recommended packages:
  libggi-target-x libggi-target libxine-extracodecs
 
The following NEW packages will be installed:
  libartsc0 libdvdread3 libfaac0 libggi2 libgii1 libgii1-target-x liblame0
  libmodplug0c2 libmp4v2-0 libmpcdec3 libungif4g libxine1 libxvidcore4
  libxvmc1 mplayer mplayer-skins totem-xine


2) Prepare for libvdcss installation.

-->System
   -->Administration
      -->Synaptic Package Manager

Enter password if asked.

>click:  "Status" button"
>select: "Not installed"
>mark for installation: "debhelper, build-essential, fakeroot"


3) Install libdvdcss2.

-->Continue in "Terminal" (and use Command line)
   -->Type command: "sudo  /usr/share/doc/libdvdread3/install-css.sh"

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
karibu@BitByter:~$ sudo  /usr/share/doc/libdvdread3/install-css.sh
Password:
--06:21:33--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_amd64.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_amd64.deb)
           => `/tmp/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 26,176 (26K) [text/plain]

100%[====================================>] 26,176         3.35K/s    ETA 00:00

06:21:45 (3.35 KB/s) - `/tmp/libdvdcss.deb' saved [26176/26176]

(Reading database ... 90521 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using /tmp/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...
karibu@BitByter:~$ 
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
Your DVD player should now play back encrypted DVDs. It worked for me;)

---

### Post by manas on 2006-11-15
hey I did as instructed but still I am getting error  saying as below


The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?



help me
](*,) ](*,) ](*,)

---

### Post by aidanr on 2006-11-15
is it just one dvd or all? i came across one dvd once that was copy protected and had the exact same problem, although that didn't stop me copying the dvd with xdvdshink:rolleyes:

---

### Post by manas on 2006-11-15
Its with all dvd 

none worked

---

### Post by PrinceArithon on 2006-11-16
Try doing it yourself with these instructions.

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_DVD_playback_capability)

Sometimes going in and doing it by hand works better than having a program do it for you.

GOOD LUCK!!!

---

