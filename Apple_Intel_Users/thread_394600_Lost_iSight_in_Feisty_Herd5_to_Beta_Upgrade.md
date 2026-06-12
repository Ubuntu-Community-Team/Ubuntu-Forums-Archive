---
title: "Lost iSight in Feisty Herd5 to Beta Upgrade"
date: 2007-03-27
forum: Apple Intel Users
---

### Post by ced on 2007-03-27
Hi all,

I'm a happy owner of withe C2D Macbook. Using Feisty Herd5, I installed iSight support using linux-uvc-0.1.0-e without any troubles.

Since the last kernel upgrade (2.6.20-12 to 2.6.20-13) I reinstalled it but I lost /dev/video0.

However, everything seems to be fine during install :

```

sudo make
Building USB Video Class driver...
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.20-13-generic »
  CC [M]  /home/cedric/Download/linux-uvc-0.1.0-e/uvcvideo.o
/home/cedric/Download/linux-uvc-0.1.0-e/uvcvideo.c: In function ‘uvc_init_isoc’:
/home/cedric/Download/linux-uvc-0.1.0-e/uvcvideo.c:1578: warning: assignment from incompatible pointer type
/home/cedric/Download/linux-uvc-0.1.0-e/uvcvideo.c: In function ‘uvc_init_status’:
/home/cedric/Download/linux-uvc-0.1.0-e/uvcvideo.c:3663: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/cedric/Download/linux-uvc-0.1.0-e/uvcvideo.mod.o
  LD [M]  /home/cedric/Download/linux-uvc-0.1.0-e/uvcvideo.ko
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.20-13-generic »

```

```

sudo make install
Installing USB Video Class driver...
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.20-13-generic »
  INSTALL /home/cedric/Download/linux-uvc-0.1.0-e/uvcvideo.ko
  DEPMOD  2.6.20-13-generic
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.20-13-generic »
depmod -ae

```

```

sudo ./extract /media/Macintosh\ HD/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport 
Apple iSight with firmware already loaded found
Apple iSight with firmware already loaded found

```

```

sudo modprobe uvcvideo

```

If I "lsmod", the driver seems to be correctly loaded :

 ```

lsmod | grep uvcvideo
uvcvideo               42500  0 
videodev               28160  1 uvcvideo
v4l1_compat            15236  2 uvcvideo,videodev
v4l2_common            25216  2 uvcvideo,videodev
usbcore               134280  10 uvcvideo,hci_usb,ndiswrapper,appleir,appletouch,usbhid,xpad,ehci_hcd,uhci_hcd

```

But :

```

ls /dev/video*
ls: /dev/video*: No such file or directory

```

Any hints ?

---

### Post by ced on 2007-03-27
Replying to myself for the record.

I found in launchpad that the bug was tracked :

[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86754](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86754)

See comment :

[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86754/comments/8](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86754/comments/8)

---

### Post by bsantos on 2007-03-27
> **ced said:**
> Replying to myself for the record.

I found in launchpad that the bug was tracked :

[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86754](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86754)

See comment :

[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86754/comments/8](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86754/comments/8)


:)

Yes, I've been waiting for someone else to complaint about this. I believe something is broken on uvc svn, the note on the last update from Ben:

  * uvcvideo: Update to latest SVN version.

This was the update (2.6.20-12 to 2.6.20-13) that broke it. It fixed other bugs though.

I didn't want to open a new bug, since Ben must be on the case. ;)

Lets just hope the next update fixes this and brings automatic firmware loading too! :D

---

