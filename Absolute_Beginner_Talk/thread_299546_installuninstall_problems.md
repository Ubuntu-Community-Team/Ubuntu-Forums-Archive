---
title: "install/uninstall problems"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Foustus on 2006-11-14
Hello everyone. Linux newbie here. I am running Ubuntu 6.10 and I am unable to install or remove anything using the Synaptic Package Manager. Bellow is the error that I get. I tried to remove Kd3 but I am unable to do so, I am unable to install or remove anything. Also I am unable to view DVDs even though I have installed libdvdread3. Would appreciate any help. Thanks

E: k3d: subprocess post-installation script returned error exit status 1

---

### Post by dannyboy79 on 2006-11-14
are you using synaptic with root privalages? also, for dvd viewing you have to install more than what you have noted. go to the doc page of ubuntu ([https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)) and find out how to watch dvd's. i would suggest a restart if synaptic is giving you weird erros. have you enabled the other repos? that's also on the doc page.

edited: or here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by Foustus on 2006-11-14
Okay. When I insert DVD Totem automaticaly comes up and gives me this:

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

Also. When installing and removing, I get this:

E: k3d: subprocess post-installation script returned error exit status 1

I followed the link you gave me and found a section on playing DVDs. Hers what I found:

 How to install DVD playback capability

ironss: gstreamer dvd plugin is available as part of plugins-bad (or ugly?) and does not work reliably. However, Totem works with the xine backend to play back DVDs. This will keep you going until gstreamer gets dvd playback. Note that you do not have to install xine-ui or mplayer as suggested in

    * Read #General Notes
    * Read #How to add extra repositories 

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

Didnt work:

frank@frank-desktop:~$ sudo apt-get install libdvdread3
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
The following packages were automatically installed and are no longer required:
  libmono2.0-cil libmono-data-tds2.0-cil libmono-system-data2.0-cil
  libxvidcore4 mplayer-skins libmp4v2-0 mplayer libsgutils1 mencoder
  libmono-cairo2.0-cil libmono-security2.0-cil libggi2 libgii1
  libmono-sqlite2.0-cil libmono-system-web2.0-cil libgii1-target-x
  libmono-sharpzip2.84-cil libmono-corlib2.0-cil libipoddevice0 cpvts libnjb5
  libmono-system2.0-cil libfaac0 libungif4g
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
frank@frank-desktop:~$ sudo usr/share/doc/libdvdread3/install-css.sh
sudo: usr/share/doc/libdvdread3/install-css.sh: command not found
frank@frank-desktop:~$ sudo apt-get install totem-xine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
totem-xine is already the newest version.
The following packages were automatically installed and are no longer required:
  libmono2.0-cil libmono-data-tds2.0-cil libmono-system-data2.0-cil
  libxvidcore4 mplayer-skins libmp4v2-0 mplayer libsgutils1 mencoder
  libmono-cairo2.0-cil libmono-security2.0-cil libggi2 libgii1
  libmono-sqlite2.0-cil libmono-system-web2.0-cil libgii1-target-x
  libmono-sharpzip2.84-cil libmono-corlib2.0-cil libipoddevice0 cpvts libnjb5
  libmono-system2.0-cil libfaac0 libungif4g
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
frank@frank-desktop:~$

---

### Post by dannyboy79 on 2006-11-14
> **Foustus said:**
>  Okay. When I insert DVD Totem automaticaly comes up and gives me this:

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss? 
ok, for this do sudo aptitude install libdvdcss

> **Foustus said:**
> 
Also. When installing and removing, I get this:

E: k3d: subprocess post-installation script returned error exit status 1
Resolved with a little trick (taken from [http://ubuntuforums.org/showthread.php?p=1706973)](http://ubuntuforums.org/showthread.php?p=1706973)).
These are the steps:
Move /usr/bin/pycentral to anywhere else (e.g.: /tmp)
Run apt-get remove k3d
Move /tmp/pycentral to /usr/bin

as a side note, when you use aptitude instead of apt-get it takes better care of dependencies and it appears that you are having dependencies issues, possibly.

> **Foustus said:**
> I followed the link you gave me and found a section on playing DVDs. Hers what I found:

 How to install DVD playback capability

ironss: gstreamer dvd plugin is available as part of plugins-bad (or ugly?) and does not work reliably. However, Totem works with the xine backend to play back DVDs. This will keep you going until gstreamer gets dvd playback. Note that you do not have to install xine-ui or mplayer as suggested in

    * Read #General Notes
    * Read #How to add extra repositories 

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

Didnt work:

frank@frank-desktop:~$ sudo apt-get install libdvdread3
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
The following packages were automatically installed and are no longer required:
  libmono2.0-cil libmono-data-tds2.0-cil libmono-system-data2.0-cil
  libxvidcore4 mplayer-skins libmp4v2-0 mplayer libsgutils1 mencoder
  libmono-cairo2.0-cil libmono-security2.0-cil libggi2 libgii1
  libmono-sqlite2.0-cil libmono-system-web2.0-cil libgii1-target-x
  libmono-sharpzip2.84-cil libmono-corlib2.0-cil libipoddevice0 cpvts libnjb5
  libmono-system2.0-cil libfaac0 libungif4g
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
frank@frank-desktop:~$ sudo usr/share/doc/libdvdread3/install-css.sh
sudo: usr/share/doc/libdvdread3/install-css.sh: command not found
frank@frank-desktop:~$ sudo apt-get install totem-xine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
totem-xine is already the newest version.
The following packages were automatically installed and are no longer required:
  libmono2.0-cil libmono-data-tds2.0-cil libmono-system-data2.0-cil
  libxvidcore4 mplayer-skins libmp4v2-0 mplayer libsgutils1 mencoder
  libmono-cairo2.0-cil libmono-security2.0-cil libggi2 libgii1
  libmono-sqlite2.0-cil libmono-system-web2.0-cil libgii1-target-x
  libmono-sharpzip2.84-cil libmono-corlib2.0-cil libipoddevice0 cpvts libnjb5
  libmono-system2.0-cil libfaac0 libungif4g
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
frank@frank-desktop:~$ 
do you have synaptic open while you are trying to install stuff? cause this error: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
isn't good. why don't you do a restart before you try all this stuff.
i found this a little lower than where you looked, Stubby: gstreamer dvd plugin not ported to dapper yet. following instructions will not work properly. 
Read #General Notes 
Read #How to add extra repositories 
sudo apt-get install libdvdcss2

also after you enable the extra repo's, did you do a sudo aptitude update and then sudo aptitude upgrade? give all this a try and I would strongly suggest you restart your xserver, you can do that by shutting everything (apps) down, then hit ctrl-alt-backspace then relogin and try everything.

---

### Post by Foustus on 2006-11-14
Okay tried the sudo aptitude install libdvdcss and heres what I got:
frank@frank-desktop:~$ sudo aptitude install libdvdcss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for libdvdcss
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up k3d (0.5.12.0-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
frank@frank-desktop:~$ 

The Synaptic Package Manager is open and I have restated several times. I dont seem to be have any other trouble except for that which is in the previous post. Thanks for your continued help.

---

### Post by dannyboy79 on 2006-11-15
> **Foustus said:**
> Okay tried the sudo aptitude install libdvdcss and heres what I got:
frank@frank-desktop:~$ sudo aptitude install libdvdcss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for libdvdcss
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up k3d (0.5.12.0-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
frank@frank-desktop:~$ 

The Synaptic Package Manager is open and I have restated several times. I dont seem to be have any other trouble except for that which is in the previous post. Thanks for your continued help.

alright, well you should learn to copy and paste instead of read and type because I never told you to install libdvdcss, i told you to install libdvdcss2, and even after it told you it couldn't find it, why wouldn't you just use the search function that is within synaptic. i don't know if you if you know this but you can't have synaptic open AND be doing sudo apt-get or sudo aptitude from the command line. that'll give you errors, that's why I asked if you had synaptic open while doing the k3d thing previously cause it said that it couldn't lock the blah blah dir. you have to use 1 or the other not both at the same time! as for the k3d error, did you first do a sudo aptitude remove k3d and sudo aptitude purge k3d? OR open up synaptic and chose to "completely remove" k3d, then after that follow the exact instructions that I posted cause according to the page I got it from that was the solution to this same error. so if that's not working than I am about out of ideas? sorry.

---

