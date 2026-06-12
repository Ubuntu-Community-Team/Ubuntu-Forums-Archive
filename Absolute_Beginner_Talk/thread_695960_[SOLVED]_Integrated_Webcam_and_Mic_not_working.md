---
title: "[SOLVED] Integrated Webcam and Mic not working"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by DamonChyld on 2008-02-13
I have been working on this all morning and am still not able to get my integrated mic/webcam working on my Dell Vostro 1500.

It appears that the fix for the webcam might be Chokas's reply on page two of thread 4204361 (our lshw and lsusb info's match), but I am stuck on the 'compile and install' step. How do you do this?

On the mic, most of the threads instruct to go into volume controls and change around settings for my 0:HDA Intel (alsa mixer). Under  Edit > Preferences I have selected Digital and Digital Input Source, Recording is turned up all the way, and Options > Input Source is Digital Mic 1 but it is still not picking up anything.

> **chokas said:**
> Hi all, I have a VOSTRO 1500

My lshw gets the following for the audio device

```
 *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

And lsusb shows the following for my webcam
```

Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
```

At first with a fresh installation of gutsy I didn't get the audio to work, so I had to update the kernel and that did the trick. I posted this in another thread so here's the link..

[http://ubuntuforums.org/showpost.php?p=4109859&postcount=37](http://ubuntuforums.org/showpost.php?p=4109859&postcount=37)

And I got the webcam to work finally today following this easy steps from the gentoo wiki

[http://gentoo-wiki.com/HARDWARE_Dell_Inspiron_1520](http://gentoo-wiki.com/HARDWARE_Dell_Inspiron_1520)

You have to do the following:

 Download svn trunk

```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
```

      Insert the id product in uvc_driver.c

/* after line 1661 */
/* OmniVision OEM Dell Notebook */
	{ .match_flags		= USB_DEVICE_ID_MATCH_DEVICE
				| USB_DEVICE_ID_MATCH_INT_INFO,
	  .idVendor		= 0x05a9,
	  .idProduct		= 0x2640,
	  .bInterfaceClass	= USB_CLASS_VIDEO,
	  .bInterfaceSubClass	= 1,
	  .bInterfaceProtocol	= 0,
	  .driver_info		= UVC_QUIRK_PROBE_MINMAX },

 Compile and install

```

make
make install
```

 Load driver

```
modprobe uvcvideo
```

AND NOW TEST IT WITH gstreamer-properties or with amsn, Ready for webcam calls :guitar: !!

amsn gave me some bugs, and a black image, but I adjusted the settings within a chat window changing my display picture and clicking on "webcam snapshot" ;), hope this helps.

Thanks for any help!

---

### Post by DamonChyld on 2008-02-13
*bump*

---

### Post by DamonChyld on 2008-02-13
Update - I think I figured out how to make ;)

I CD'd to the directory uvc_driver.c was in and ran sudo make, sudo make install (even managed to troubleshoot initial error messages, I am so proud ;) but modprobe uvcvideo does not give any output. 

I hope this will help illuminate something ;)

damien@laptop:~/trunk$ sudo make
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/damien/trunk/uvc_driver.o
  CC [M]  /home/damien/trunk/uvc_queue.o
  CC [M]  /home/damien/trunk/uvc_v4l2.o
  CC [M]  /home/damien/trunk/uvc_video.o
  CC [M]  /home/damien/trunk/uvc_ctrl.o
  CC [M]  /home/damien/trunk/uvc_status.o
  CC [M]  /home/damien/trunk/uvc_isight.o
  LD [M]  /home/damien/trunk/uvcvideo.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/damien/trunk/uvcvideo.mod.o
  LD [M]  /home/damien/trunk/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

damien@laptop:~/trunk$ sudo make install
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/damien/trunk/uvcvideo.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
depmod -ae

damien@laptop:~/trunk$ sudo modprobe uvcvideo
damien@laptop:~/trunk$ modprobe uvcvideo

---

### Post by DamonChyld on 2008-02-13
*bump*

---

### Post by DamonChyld on 2008-02-14
Ok, just got my mic working (I have the STAC 9205) by going into applications> sound recorder and changing input to ACDMux. It changed back to InVol after a restart but seems to be stable now... hope this thread will help someone!

---

