---
title: "Acer Notebook Suyin webcam works"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by colinb on 2007-11-01
Just installed gutsy, then followed this thread and my Acer CrystalEye webcam (064e:a101) works.  This also suppose to work with feisty.

[http://rafeequl.wordpress.com/2007/10/15/acer-crystaleye-webcam-on-linux-ubuntu/#comment-38](http://rafeequl.wordpress.com/2007/10/15/acer-crystaleye-webcam-on-linux-ubuntu/#comment-38)

Can you tell me how to do this step:

To make it user-friendly, create a Custom Application Launcher pointed to this script:

    #!/bin/bash
    # will place snapshots in Desktop
    cd ~/Desktop
    # will produce pnm: Netpbm PPM “rawbits” image data,
    # instead of default MJPEG format that the webcam does not support
    luvcview -f yuv

How do I make a script

---

### Post by akwatve on 2008-01-15
I created a desktop link instead.... which is equally good.
In fact you may even add it to KMenu (I use kde)

Here are details od my desktop launcher :
FIlename ~/Desktop/Webcam.desktop

Note: I am using camorama's icon... Also set Path to the default path u want to use

cat  ~/Desktop/Webcam.desktop
>>
[Desktop Entry]
Comment=Finally my webcam is up
Comment[en_US]=Finally my webcam is up
Encoding=UTF-8
Exec=luvcview -f yuv
GenericName=Webcam
GenericName[en_US]=Webcam
Icon=/usr/share/pixmaps/camorama.png
MimeType=
Name=WebCam
Name[en_US]=WebCam
Path=~/Desktop/
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DCOP-ServiceType=
X-KDE-SubstituteUID=false
X-KDE-Username=

Hope this helps...

---

