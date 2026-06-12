---
title: "isight macbook3,1 10.04"
date: 2010-05-09
forum: Apple Hardware Users
---

### Post by xxander on 2010-05-09
Once I download and install isight-firmware-tools... im supposed to redirect it somewhere... i tried keeping the default thing set, but it failed to install that way.. any suggestions (MacBook 3,1. 10.04 LTS)

---

### Post by Zeckman on 2010-05-11
This is quite simple to sort out (also currenty testing Ubuntu on a MacBook3-1)

Download the isight firmware from this link::

[http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz](http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz)

extract it to a directory... forget about the script and patch files, just run the isight firmware extraction tool from synaptic again. If you have tried to install before, do a complete removal of the tool and re-install. When it asks for the firmware, point it to the extracted file in the firmware directory. Once done all should work and you wont have the firmware error on booting.

Have everything working perfectly on my MacBook3-1. For perfect TouchPad interaction don't forget to install 'gsynaptics' from synaptic package manager. Just turn the sensitivity to pretty much full, and enable 'faster double tapping'... also for better bluetooth control install 'bluman'&'bluetooth'. Un-install 'gnome-bluetooth'.

The only issue I have is to do with Grub2 and Plymouth. Grub will not show, and plymouth ain't showing no startup animation... Starting to miss Xsplash and Usplash :( Should of seen my previous 9.10 setup ;) Does the animated logo show up when u boot? (solved all these issues and have written scripts to help adjust GDM, Grub2 and plymouth animated boot.. now have my custom Boot Mac anim running beautifully)

hope this help

Mike
(zeckman)

---

### Post by AlexKoktas on 2011-04-16
> **Zeckman said:**
> This is quite simple to sort out (also currenty testing Ubuntu on a MacBook3-1)

Download the isight firmware from this link::

[http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz](http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz)

extract it to a directory... forget about the script and patch files, just run the isight firmware extraction tool from synaptic again. If you have tried to install before, do a complete removal of the tool and re-install. When it asks for the firmware, point it to the extracted file in the firmware directory. Once done all should work and you wont have the firmware error on booting.

Have everything working perfectly on my MacBook3-1. For perfect TouchPad interaction don't forget to install 'gsynaptics' from synaptic package manager. Just turn the sensitivity to pretty much full, and enable 'faster double tapping'... also for better bluetooth control install 'bluman'&'bluetooth'. Un-install 'gnome-bluetooth'.

The only issue I have is to do with Grub2 and Plymouth. Grub will not show, and plymouth ain't showing no startup animation... Starting to miss Xsplash and Usplash :( Should of seen my previous 9.10 setup ;) Does the animated logo show up when u boot? (solved all these issues and have written scripts to help adjust GDM, Grub2 and plymouth animated boot.. now have my custom Boot Mac anim running beautifully)

hope this help

Mike
(zeckman)

It worked for me, too. Thank you very much, Zeckman :)

---

