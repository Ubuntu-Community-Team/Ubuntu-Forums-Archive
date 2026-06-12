---
title: "Another Webcam problem thread"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by emnaki on 2007-07-14
I'm trying to get the webcam which came with my new Samsung Q45 notebook to work with no success. I've tried all of the proposed solutions that I've been reading about here like easycam and gspca.

Below are some of the details:
```

kchik@kchik:/usr/src/modules/spca5xx$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0ac8:c302 Z-Star Microelectronics Corp.  <--- I assume this is my webcam
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 15ca:00c3  
Bus 002 Device 001: ID 0000:0000  

```

```

kchik@kchik:/usr/src/modules/spca5xx$ lsmod | grep gsp
gspca                 642896  0 
videodev               28160  2 gspca,uvcvideo
usbcore               134280  7 gspca,uvcvideo,usbhid,hci_usb,ehci_hcd,uhci_hcd

```

```

kchik@kchik:/usr/src/modules/spca5xx$ ls /dev/vid*
ls: /dev/vid*: No such file or directory

```

So is it just that there is no way of getting my Webcam to work in Linux or are there anything else I could still try? Also camstream tells me it can't find the device which ofcourse is natural since no video files exist in /dev/

---

### Post by emnaki on 2007-07-16
bump

---

### Post by tcoffeep on 2007-07-16
I've always been told that webcams aren't too compatible with Ubuntu.

[edit] try looking in the laptop section...

---

### Post by jose Lang on 2007-07-17
You can get the camera to work (only tested with ekiga) using the new UVC driver. I have added the link for download to the Q45 laptop testing page on the wiki.

I will add the details of how to set it up when I get some time.

Jose

---

### Post by emnaki on 2007-07-18
Thanks for the help. I've followed the instructs on the driver page, everything compiled successfully, the usb device seems to be detected.
```

kchik@kchik:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-generic)
looking for available devices
port 73-88
    type : Xvideo, image scaler
    name : Intel(R) Textured Video

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : Vega USB 2.0 Camera.
    flags:  capture  

```

But I am still not able to get the camera to work:
```

kchik@kchik:~$ luvcview
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 22.
 Init v4L2 failed !! exit fatal 

```

Is there anything I could try to get it working?

---

### Post by jose Lang on 2007-07-19
I still get error messages in xawtv but the camera should work ok in ekiga.

---

### Post by linux4africa on 2008-01-10
I installed "ucview" without reinstalling the usb drivers and it worked out of the box.

See:
[http://www.astronomycamerasblog.com/2007/11/28/usb-20-astronomy-cameras-on-ubuntu-704-feisty-fawn/](http://www.astronomycamerasblog.com/2007/11/28/usb-20-astronomy-cameras-on-ubuntu-704-feisty-fawn/)

Vega camera (vimicro) on Samsung R70 with Ubuntu 7.10.

xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
looking for available devices
/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : Vega USB 2.0 Camera.
    flags:  capture

---

### Post by aktiwers on 2008-01-10
Have you looked here?
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

