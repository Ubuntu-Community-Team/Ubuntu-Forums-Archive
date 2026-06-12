---
title: "logitech express"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by vista on 2006-08-07
I've got a logitech express cam 046d:0850 that i'm trying to use with amsn, i've also installed ubuntu dapper, is my webcam going
to be recognized as soon as i start up dapper, or do I have to do all this : > USB ID 046d:0850 Make sure the build-essential package and the 
correct linux-headers package are installed. 
Install the package qc-usb-source, 
uncompress the archive /usr/src/qc-usb-modules.tar.gz 
and execute /usr/src/modules/qc-usb-source/quickcam.sh 
(Note: The driver is reliable and included in other 
distributions like Mandriva, it could be included in Ubuntu as well)
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras")
If someone could advise how to set up my webcam it would be greatly appreciated.

Also on a sidenote, I'm trying to set up a wireless usb adapter,
dwl-g132, like this :> 
Code:
$ cd /wlan 
$ ndiswrapper -i athfmwdl.inf 
$ ndiswrapper -i NetA5AGU.inf

i've put the wlan folder on my desktop and not under /. 
How do i cd the wlan folder on my desktop?

---

