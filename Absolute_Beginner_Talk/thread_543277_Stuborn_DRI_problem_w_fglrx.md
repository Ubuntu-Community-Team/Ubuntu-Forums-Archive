---
title: "Stuborn DRI problem w/ fglrx"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by mnb on 2007-09-04
Ok... I've installed and de-installed the fglrx driver multiple times, and followed up on every troubleshooting thread I can find here... all in vain.  I still can't get the driver to load properly - I'm getting the Mesa messages when running fglrxinfo instead of references to my ATI Radeon M300 card on my IBM T43 Thinkpad.  I'm currently on "Step 4" of this post: [http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283) and wondering if I have a linking problem... but can't tell for sure.

Could someone *please* help me sort thru this conflicting and confusing issue?  Here are some of my results:  (I'm attaching my compete Xorg.0.log file as well).  A *BIG* thanks to any kind soul who can help me work thru this confusing maze.

====   Xorg.0.log  =======

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


/usr/lib/xorg/modules$ ls -la | grep dri
lrwxrwxrwx 1 root root      13 2007-09-03 17:44 dri -> /usr/lib/dri/

/usr/X11R6/lib/modules$ ls -la | grep dri
drwxr-xr-x 2 root root 4096 2007-09-01 20:45 dri

/usr/lib$ ls -la | grep dri
drwxr-xr-x   2 root root     4096 2007-09-03 18:00 dri

===== xorg.conf ====
Section "DRI"
	Mode         0666
EndSection

---

### Post by mnb on 2007-09-09
Hi all,

Doesn't anybody have any ideas on this?  

Does it look like my symbolic links are OK?  Are there any clues in my log file that I attached?

Any help at all would be greatly appreciated.

Thanks,

Michael

---

### Post by mjpolifka on 2007-09-18
I also have a problem loading DRI.  In fact, when i try to load it manually (I think that's what I'm trying here, I'm rather new at this) I get:

mitch@mitch-desktop:~$ sudo modprobe dri
FATAL: Module dri not found.

I added these symbolic links during installation:
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
sudo mkdir -p /usr/X11R6/lib/modules/dri  
sudo ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri

---

