---
title: "Wecam problems on 7.10"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Jaysont34 on 2007-10-19
Hi, I am new to Linux and really have no experience what so ever, besides what I have learned in the past couple of days. 

I have an Asus S96S laptop, and my first fear when installing Linux was hardware issues since laptops tend to have very specific drivers. Everything seems to be working great (was actually amazed by the fact that Linux was able to recognize my laptop shortcut keys, like volume, contrast, etc., not like windows :) ).

Well, almost everything actually, I can't get my webcam to work, and I have been going nuts over it for the past couple of days. I searched the forums, google, tried everything I found, but nothing, Easycam2 keeps telling me "No camera, no compatible camera found", Camorama says "Could not connect to video device (/dev/video0). Please check connection."  I tried everything from over [[COLOR="RoyalBlue"]here[/COLOR]]("https://help.ubuntu.com/community/Webcam?highlight=%28CategoryDocumentation%29") .  I also tried the Linux UVC driver from [[COLOR="RoyalBlue"]here[/COLOR]]("http://linux-uvc.berlios.de/#download").

I am completely stumped, I'm just about to give up on it, so I am coming here for 1 last try :).  I managed to figure out the model of the webcam, [Genesys Logic GL860A]("http://www.genesyslogic.com/_en/product_01_1.php?id=59").  Here is my lsusb info:

 Bus 007 Device 003: ID 05e3:f192 Genesys Logic, Inc. <----Webcam
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 004 Device 001: ID 0000:0000

Thanks in advance for any help, please tell me if you need any more info.

---

### Post by natman on 2007-10-19
I was able to use my webcam using a problem called "ekiga" but since gusty pidgeon ( used to be gaim ) now see the cam

---

### Post by Jaysont34 on 2007-10-19
> **natman said:**
> I was able to use my webcam using a problem called "ekiga" but since gusty pidgeon ( used to be gaim ) now see the cam

Thanks for the tip, just tried it, but when I get to the video settings part of the setup, it says I have no video input devices, in other words, Linux doesn't even know that the webcam is there, even though it appears in lsusb.

---

### Post by jon_gunnar on 2007-10-20
> **Jaysont34 said:**
> Thanks for the tip, just tried it, but when I get to the video settings part of the setup, it says I have no video input devices, in other words, Linux doesn't even know that the webcam is there, even though it appears in lsusb.

Not much help in me cause I got the same problem with a Creative Live MOTION camera.
It's found,but there has not been created any /dev/video* nodes.```


jon@jon-desktop:~$ lsusb
Bus 006 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 045e:00f9 Microsoft Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 041e:4041 Creative Technology, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05e3:0760 Genesys Logic, Inc. Card Reader
Bus 001 Device 001: ID 0000:0000
```

---

### Post by Dandalf on 2007-11-24
bump, having same problem with Creative Live! IM webcam

---

### Post by philinux on 2007-11-24
You need to install the gspca driver for your cam if it's supported. You complile it.

Here's the link you need. 

According to the guru of webcams check out your cam for support.

[http://mxhaard.free.fr](http://mxhaard.free.fr)

[http://ubuntuforums.org/showthread.php?t=621164&page=2](http://ubuntuforums.org/showthread.php?t=621164&page=2) this thread has all the compile stuff too.

---

### Post by theZoid on 2008-01-26
> **Jaysont34 said:**
> Hi, I am new to Linux and really have no experience what so ever, besides what I have learned in the past couple of days. 

I have an Asus S96S laptop, and my first fear when installing Linux was hardware issues since laptops tend to have very specific drivers. Everything seems to be working great (was actually amazed by the fact that Linux was able to recognize my laptop shortcut keys, like volume, contrast, etc., not like windows :) ).

Well, almost everything actually, I can't get my webcam to work, and I have been going nuts over it for the past couple of days. I searched the forums, google, tried everything I found, but nothing, Easycam2 keeps telling me "No camera, no compatible camera found", Camorama says "Could not connect to video device (/dev/video0). Please check connection."  I tried everything from over [[COLOR="RoyalBlue"]here[/COLOR]]("https://help.ubuntu.com/community/Webcam?highlight=%28CategoryDocumentation%29") .  I also tried the Linux UVC driver from [[COLOR="RoyalBlue"]here[/COLOR]]("http://linux-uvc.berlios.de/#download").

I am completely stumped, I'm just about to give up on it, so I am coming here for 1 last try :).  I managed to figure out the model of the webcam, [Genesys Logic GL860A]("http://www.genesyslogic.com/_en/product_01_1.php?id=59").  Here is my lsusb info:

 Bus 007 Device 003: ID 05e3:f192 Genesys Logic, Inc. <----Webcam
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 004 Device 001: ID 0000:0000

Thanks in advance for any help, please tell me if you need any more info.

It's been a while, but did you ever get that Genesys Logic webcam working?  That's what I have in my Asus laptop (sig).  Please report back if you have.  thanks!

---

### Post by albert_chuang on 2008-02-18
Hi Jaysont,

Could you report the 'lsusb -v -d 05e3:f192' and your status to linux-uvc-devel mailing list ?
These day has new patch, refer here [[COLOR="Blue"][Linux-uvc-devel][/COLOR] [COLOR="Blue"][PATCH] [uvcvideo] Add GenesysLogic with UVC_QUIRK_STREAM_NO_FID[/COLOR]]("https://lists.berlios.de/pipermail/linux-uvc-devel/2008-February/003070.html")
and [[COLOR="Blue"][Linux-uvc-devel][/COLOR] [COLOR="Blue"][PATCH] [uvcvideo] Add a testquirk module param[/COLOR]]("https://lists.berlios.de/pipermail/linux-uvc-devel/2008-February/003060.html").

you can use new patch testquirk module to try 
or you can simply edit uvc_driver.c and modify Syntek .idVendor and idVendor to
05e3:f192. And try it, waiting for your report.

this is a example in uvc_driver.c

        /* Syntek (HP Spartan) */
        { .match_flags          = USB_DEVICE_ID_MATCH_DEVICE
                                | USB_DEVICE_ID_MATCH_INT_INFO,
         .idVendor             = [COLOR="Red"]0x05e3[/COLOR],// 0x174f,
         .idProduct            = [COLOR="Red"]0xf192[/COLOR],//0x5212,
          .bInterfaceClass      = USB_CLASS_VIDEO,
          .bInterfaceSubClass   = 1,

God bless you,
albert

> **Jaysont34 said:**
> Hi, I am new to Linux and really have no experience what so ever, besides what I have learned in the past couple of days. 

I have an Asus S96S laptop, and my first fear when installing Linux was hardware issues since laptops tend to have very specific drivers. Everything seems to be working great (was actually amazed by the fact that Linux was able to recognize my laptop shortcut keys, like volume, contrast, etc., not like windows :) ).

Well, almost everything actually, I can't get my webcam to work, and I have been going nuts over it for the past couple of days. I searched the forums, google, tried everything I found, but nothing, Easycam2 keeps telling me "No camera, no compatible camera found", Camorama says "Could not connect to video device (/dev/video0). Please check connection."  I tried everything from over [[COLOR="RoyalBlue"]here[/COLOR]]("https://help.ubuntu.com/community/Webcam?highlight=%28CategoryDocumentation%29") .  I also tried the Linux UVC driver from [[COLOR="RoyalBlue"]here[/COLOR]]("http://linux-uvc.berlios.de/#download").

I am completely stumped, I'm just about to give up on it, so I am coming here for 1 last try :).  I managed to figure out the model of the webcam, [Genesys Logic GL860A]("http://www.genesyslogic.com/_en/product_01_1.php?id=59").  Here is my lsusb info:

 Bus 007 Device 003: ID 05e3:f192 Genesys Logic, Inc. <----Webcam
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 004 Device 001: ID 0000:0000

Thanks in advance for any help, please tell me if you need any more info.

---

### Post by Jack Malmostoso on 2008-02-26
Hello albert,

I have a webcam with USB ID 05e3:0503 and I think it has the same chipset. I have tried the latest svn snapshot and edited the uvc_driver.c file to include my ID.
It compiled perfectly and I could modprobe the module but luvcview does not seem to like the webcam.
Do you know if it is needed to add an udev rule by hand, or should the /dev/video0 device be created automagically?

Thanks!

---

### Post by blazercist on 2008-02-26
I also have the same Genesys Logic Webcam 
lsusb reports:
Bus 005 Device 002: ID 05e3:0503 Genesys Logic, Inc. 

I also downloaded and installed uvcvideo driver from svn as detailed and also modified uvc_driver.c to match my vendor and product ids however uvcvideo is not loaded by default... lsmod | grep uvc yeilds no result. Doing sudo modprobe uvcvideo works and then uvcvideo is listed in lsmod but the camera is still not recognized.  camorama complains of no /dev/video0 device, luvcview fails as well with "ERROR opening V4L interface : No such file or directory"

I would also like to know how to possibly get this working under ubuntu... thanks

---

### Post by Kytrix on 2008-02-27
**blazercist**>

I have the same webcam 05e3:0503 on a Asus S37S,

I try the same thing you did (but in my case i try in a virtualbox ubuntu..)
I arrived to the same result: no autoload of uvcvideo .. and no device créated after manual loading ..

**Jack Malmostoso**>
yes /dev/video0 might be auto created if webcam were recognized :/


I had already contact spca drivers developper to ask him if webcam could be supported and after look at lsusb/windows inf he said that the chipset was unknow :/


dammed webcam ! :(

Kytrix

---

### Post by Gemmer on 2008-02-28
Same here :(


Bus 005 Device 003: ID 05e3:0503 Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 147e:2016  
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:0a02 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 001 Device 001: ID 0000:0000

---

### Post by albert_chuang on 2008-02-29
Hi...
see this..
[[[COLOR="Blue"]Linux-uvc-deve[/COLOR]l] Bus 002 Device 003: ID 05e3:0503 Genesys Logic, Inc.]("http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg02459.html")

[[COLOR="Blue"]Genesys Logic[/COLOR]]("http://www.genesyslogic.com.tw/_en/product.php?classid=7")
 has two chips GL860 and GL860A. only GL860A support UVC.

so.. maybe need vendor provide the driver to support Linux ..

---

### Post by blazercist on 2008-02-29
driver support ftw, actually this cam is the only thing in my notebook which wasnt supported by default so i shoudn't complain. o well maybe they will figure this out in like a year.

---

### Post by Jack Malmostoso on 2008-02-29
> **albert_chuang said:**
> only GL860A support UVC.

Ah thank you for this information. 
Well I guess I won't be using my webcam, it was just a matter of (foolish) pride.

Bye!

---

### Post by Jack Malmostoso on 2008-04-02
> **Jack Malmostoso said:**
> Ah thank you for this information. 
Well I guess I won't be using my webcam, it was just a matter of (foolish) pride.

Bye!

Daniel Drake is working on a driver for Genesys Logic 05e3:0503. His git server is here:

git://projects.reactivated.net/~dsd/gl860.git

Snapshots here:

[http://projects.reactivated.net/snapshots/gl860/](http://projects.reactivated.net/snapshots/gl860/)

His blog:

[http://www.reactivated.net/weblog/](http://www.reactivated.net/weblog/)

If someone can lend him a hand, he'll appreciate for sure.

---

### Post by blazercist on 2008-04-14
> **Jack Malmostoso said:**
> Daniel Drake is working on a driver for Genesys Logic 05e3:0503. His git server is here:

git://projects.reactivated.net/~dsd/gl860.git

Snapshots here:

[http://projects.reactivated.net/snapshots/gl860/](http://projects.reactivated.net/snapshots/gl860/)

His blog:

[http://www.reactivated.net/weblog/](http://www.reactivated.net/weblog/)

If someone can lend him a hand, he'll appreciate for sure.

I tried this, I installed libusb-1.0 and downloaded and compiled the gl860 apps from git but I get errors when trying to run the executables. namely errors from libusb:

libusb:error [initialize_device] read failed ret=-1 errno=9
couldn't open device

---

### Post by blazercist on 2008-04-30
has anyone tried ndiswrapper on this cam?  im interested in trying it but im having trouble finding the windoze driver.

---

### Post by Jack Malmostoso on 2008-05-10
> **blazercist said:**
> has anyone tried ndiswrapper on this cam?  im interested in trying it but im having trouble finding the windoze driver.

I don't think you can use ndiswrapper with anything but wireless cards drivers. If you have any other pointers, please share them.
A driver is here:

[ftp://ftp.littlebit.ch/Littlebit%20Systems/Notebook/Sepia%20X35%20(Z37E)/Driver/Windows%20XP/11_Camera_Vista_070528.zip](ftp://ftp.littlebit.ch/Littlebit%20Systems/Notebook/Sepia%20X35%20(Z37E)/Driver/Windows%20XP/11_Camera_Vista_070528.zip)

---

### Post by blazercist on 2008-05-18
Yea you're right ndiswrapper is only for ethernet/wireless cards... still waiting patiently for a kernel driver for this cam from Danial Drake...

Like I said I tried his user space apps for capturing images from the cam but it came back with libusb errors which I cannot seem to fix..

---

### Post by Jack Malmostoso on 2008-06-01
Hi everyone,

check out this driver:

[http://sourceforge.net/projects/gl860](http://sourceforge.net/projects/gl860)

works for me! Help by providing logs!

---

### Post by theZoid on 2008-06-01
> **Jack Malmostoso said:**
> Hi everyone,

check out this driver:

[http://sourceforge.net/projects/gl860](http://sourceforge.net/projects/gl860)

works for me! Help by providing logs!

Great....point to install instructions for Hardy?  thanks

---

### Post by Jack Malmostoso on 2008-06-02
> **theZoid said:**
> Great....point to install instructions for Hardy?  thanks

Here's some quick instructions to test the driver. These instructions work as tested on an Hardy Heron livecd.

1) Install all required packages, i.e. linux-headers and build-essential. Make sure the linux-headers version matches the linux-image version.

2) Download the driver from [https://sourceforge.net/project/showfiles.php?group_id=229562](https://sourceforge.net/project/showfiles.php?group_id=229562)
There are three files linked:

- nvgl_0.1b.tgz contains the driver
- gl860-dev-0503ms.c is a "special" version of the driver tailored on my particular camera
- relog.c is a log analyzer

3) Untar the .tgz archive. Inside you'll find (among others):

- gl860-dev-0503.c
- gl860-dev-0503a.c
- gl860-dev-0503b.c

The first and second files are identical, while version "b" is different. So you have three versions to try out:

- gl860-dev-0503a.c
- gl860-dev-0503b.c
- gl860-dev-0503ms.c

4) Open a terminal window and navigate to the nvgl directory. Once there type```
$ make -f Makefile.standalone
```

5) Once compilation is done, you'll have a gl860.ko file. That is the kernel module. Copy the kernel module over to the modules directory```
$ sudo cp gl860.ko /lib/modules/`uname -r`/kernel/drivers/media/video
```and then create the module dependencies```
$ sudo depmod -a /lib/modules/`uname -r`/kernel/drivers/media/video/gl860.ko
```Now insert the driver```
$ sudo modprobe gl860
```The led on your camera should briefly turn on. Open a webcam program (camorama and/or cheese are easily installable through synaptic) and if you can see some images, rejoice!

6) In case the driver does not work, you still have two versions to try out. To do this remove the driver```
$ sudo modprobe -r gl860
```and then delete it from the modules directory```
$ sudo rm -fr /lib/modules/`uname -r`/kernel/drivers/media/video/gl860.ko
```Go back to the nvgl directory and build the new module```
$ make -f Makefile.standalone clean
$ cp gl860-dev-0503b.c gl860-dev-0503.c
$ make -f Makefile.standalone
```At this point you'll have a new gl860.ko file. Wash, rinse, repeat as above. You are encouraged to reboot after each test, just to minimize the possibility of cocking it up.
Report back any failure or success: in every case obtaining logs is very important to improve the driver!

---

### Post by nol_faich on 2008-06-04
Hi everybody (and Malmostoso :))

If the driver don't work, I think it is necessary to shutdown the computer and to start it at least some seconds after the halt in order to avoid bad behaviour of the webcam due to misunderstood instructions from the previous test.

However there is a need for at least 3 three different drivers to manage the 0503. So if it's doesn't work with the different versions, we need logs made with Windows.

---

### Post by blazercist on 2008-06-05
ive tried all three and none of them work, the light comes on and camorama just freezes, cheese just shows me the multicolored screen, i tried restarting each time.

version b was the only one that didn't hang on modprobe or cause startup problems... although it didnt work it seemed to cause the least problems...


here is the output from mencoder tv:// -tv driver=v4l2:width=640:height=480:fps=10:outfmt=bgr24:device=/dev/video0 -nosound -ovc lavc -o out.avi

MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Genesys gl860 USB Video Camera
 Capabilites:  video capture  read/write  streaming
 supported norms: 0 = webcam;
 inputs: 0 = USB;v4l2: ioctl get input failed: Invalid argument

 Current input: 1
 Current format: BGR24
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
[V] filefmt:9  fourcc:0x42475218  size:640x480  fps:10.00  ftime:=0.1000
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: BGR 24-bit)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using BGR 24-bit as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x880f730]SwScaler: using unscaled bgr24 -> yuv420p special converter
videocodec: libavcodec (640x480 fourcc=34504d46 [FMP4])
Selected video codec: [rawbgr24] vfm: raw (RAW BGR24)
==========================================================================
Forcing audio preload to 0, max pts correction to 0.
v4l2: select timeout

Skipping frame!
Pos:   0.0s      1f ( 0%)  0.76fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.03fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.16fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s      4f ( 0%)  1.25fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.30fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.34fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s      7f ( 0%)  1.38fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.39fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.42fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     10f ( 0%)  1.43fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.44fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     12f ( 0%)  1.45fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.46fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.46fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     15f ( 0%)  1.48fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.48fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.49fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     18f ( 0%)  1.50fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.49fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.50fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     21f ( 0%)  1.50fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.50fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     23f ( 0%)  1.51fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.51fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.51fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     26f ( 0%)  1.51fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.52fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.52fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     29f ( 0%)  1.52fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.52fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     31f ( 0%)  1.53fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.53fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.52fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     34f ( 0%)  1.53fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.53fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.53fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     37f ( 0%)  1.53fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.53fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.54fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     40f ( 0%)  1.54fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.54fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     42f ( 0%)  1.54fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.54fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
v4l2: select timeout( 0%)  1.54fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     45f ( 0%)  1.54fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
v4l2: select timeout( 0%)  1.54fps Trem:   0min   0mb  A-V:0.000 [0:0]

Skipping frame!
Pos:   0.0s     47f ( 0%)  1.55fps Trem:   0min   0mb  A-V:0.000 [0:0]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:      nan kbit/s  (-2147483648 B/s)  size: 0 bytes  0.000 secs  47 frames
v4l2: select timeout

---

### Post by Jack Malmostoso on 2008-06-06
Dear Blazercist,

do you have windows installed on your machine? Unfortunately the logs captured under windows are invaluable to understand how the webcam works.
If you have it installed, try capturing some logs with SniffUSB. Here are some instructions, since in the README some of it is still in french.

1. Download SniffUSB: [http://www.pcausa.com/Utilities/UsbSnoop/SniffUSB-x86-2.0.0006.zip](http://www.pcausa.com/Utilities/UsbSnoop/SniffUSB-x86-2.0.0006.zip)
You need .NET framework to have it running.

2. Disable the webcam in Control Panel --> System --> Hardware --> Device Manager --> Double click on the webcam --> Select "Disable" in the drop-down menu at the bottom of the tab.

3. Shut down the machine. Wait a few seconds. Power up the machine again and boot windows.

4. Start SniffUSB, install the filter for the webcam (it's all in the interface, don't worry) and start the log capturing. Go back to the hardware settings and reenable the camera. Capture for a few more seconds then stop the log. Click on "View log" and save it somewhere with a recognizable name.

5. Clear the log, start the capture again and start the webcam viewing software. Let it run for a few seconds (about 5" or the log will be HUGE), close the program, stop the capture. Save the log with another well recognizable name.

6. Repeat this procedure for a few more times, each time changing one (and ONLY one!) parameter of the image. For example, change the brightness by 20 points. Save the log and write down the minimum value for that parameter, the maximum, the default value, the value you started from and the value you ended up with. Again, it's tedious but it's worth it.

7. Do the same thing with the resolutions your camera is capable of. Write down the default resolution and the resolution you switch to.

8. At this point you'll have a nice selection of logs, each of which is probably about 300MB. Don't worry.

9. Move these logs to your linux installation. In the driver package there is a file called relog.c. This is a neat software that will clean up the logs leaving only the relevant information for Nol :)

10. Put the logs and relog.c in a directory. Compile relog.c ```
$ g++ relog.c -o relog
```and you'll obtain an executable named relog. Assuming that all logs you took have the extension .log, just type this to have them all automagically processed```
$ cd /directory/with/logs/and/relog
$ for i in $(ls ¦ grep .log); do ./relog $i msc; done
```
You'll end up with a bunch of .bmp images, a bunch of $i.loglog files and the most important ones, $i.c files. These are the files that are *really* needed to create the driver. Pack them up (make sure they have representative names and include a README file with some additional explanation if needed) and make them available to Nol, along with the output of```
$ lshw | grep Genesys -A3 -B1
```and the model of the laptop you have. If it's an external webcam, include the model of that too.

After this the ball is in Nol's field... just wait patiently and hopefully your webcam will work fine like mine!

@Nol: sorry I am charging you with this work ;)

---

### Post by blazercist on 2008-06-06
I wish I could help, but I exclusively using linux, I haven't used windows in over a year.

The laptop I'm using is the Asus C90s and the cam is built-in.  If there are any logs or tests I could perform for you under linux I would be more than happy to help.

Please keep up the good work and hopefully soon we will all have a working driver.

Jack, out of curiousity what type of machine/OS(kernel) do you have?  Do you have the 0503 version of the camera?  Which version (a,b,c,ms) worked for you?

---

### Post by Jack Malmostoso on 2008-06-06
I have an Asus Z37E and I myself only use linux... I installed windows just for the purpose of the logs!
I am on Debian Sid AMD64 and my camera is the 05e3:0503 version, and the version "ms" is actually written starting from my logs.
As Nol figured out, it seems that every damn camera needs a specific driver... the last published driver (version 0.1d) works perfectly for me (see here: [http://forum.ubuntu-fr.org/viewtopic.php?id=194602&p=4](http://forum.ubuntu-fr.org/viewtopic.php?id=194602&p=4)) but it does not seem the case for others...

Mystery, and crappy hardware for sure...

---

### Post by blazercist on 2008-06-06
I'm both happy and a little upset, I was looking forward to this actually working, its the only thing besides audio over HDMI and a few FN+ keys that doesn't work on my laptop.  When I saw your post I thought I would be one step closer.  But I am happy that progress is being made.  I don't have any working Windows CD's much less any serial numbers for them.. too bad I could have had nol make me my own custom driver ;) .  I guess I'll just have to wait.  You may want to update your instructions post as the 0.1d version doesn't have a "0503b.c" and you also may want to make a seperate thread with the driver link and a how to, perhaps the thread will get more hits and you will get more feedback that way.

---

### Post by Jack Malmostoso on 2008-06-07
Blazercist, could you provide the output of ```
$ sudo lshw | grep Genesys -A3 -B1
```I'd like to check which revision of the camera you have. It is really funny that out of three people for whom the driver works, we need three different drivers.
As for the rest, I guess I'll take some time to write a couple of lines of HTML to create a proper homepage for the gl860 project, since Nol is busy actually coding :)
Sorry for not being able to help further... stay tuned!

---

### Post by nol_faich on 2008-06-07
On [https://sourceforge.net/projects/gl860/]("https://sourceforge.net/projects/gl860/"), 
I uploaded a new version of the different drivers for 0503.
Please let me now if it works.
Theoretically :
- Version "ms" : Asus Z37E
- Version "sim" : Medion
- Version "a" : other
If a version does not work, try another one.

---

### Post by blazercist on 2008-06-08
> **Jack Malmostoso said:**
> Blazercist, could you provide the output of ```
$ sudo lshw | grep Genesys -A3 -B1
```I'd like to check which revision of the camera you have. It is really funny that out of three people for whom the driver works, we need three different drivers.
As for the rest, I guess I'll take some time to write a couple of lines of HTML to create a proper homepage for the gl860 project, since Nol is busy actually coding :)
Sorry for not being able to help further... stay tuned!

The above command gives no output, I tried without the grep and read through and didn't see anything referencing the webcam,

lsusb -v outputs

Bus 005 Device 002: ID 05e3:0503 Genesys Logic, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05e3 Genesys Logic, Inc.
  idProduct          0x0503 
  bcdDevice            1.03
  iManufacturer           0 
  iProduct                1 USB 2.0 PC Camera
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          129
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              140mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               5
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               5
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               5
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0c00  2x 1024 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               5
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

The new "a" version of the driver does not work for me, I will try ms and sim  a little later.

---

### Post by nol_faich on 2008-06-08
Don't care about the lshw. All webcam send the same informations even they need a different driver.

A new release is available via [https://sourceforge.net/projects/gl860/]("https://sourceforge.net/projects/gl860/"). 
Hope it will help you.

---

### Post by nol_faich on 2008-06-10
Does any one tried the last release of SourceForge ??

[https://sourceforge.net/project/showfiles.php?group_id=229562]("https://sourceforge.net/project/showfiles.php?group_id=229562")

---

### Post by blazercist on 2008-06-10
I haven't had a chance yet, I will try it after work and tell you if anything changed...  just one question... I read that I have to restart only between changing driver versions is that correct or do I have to restart once the driver is installed before testing it?

---

### Post by nol_faich on 2008-06-10
A driver which is not suitable for the webcam send bad commands to the webcam so that it can not work properly if you test another driver. 
To avoid such an effect, the webcam must be reset. So once the driver is installed, you need to shutdown the computer.
For example, in the case of Malmostoso's webcam, the driver has been working only after the restart. Before the shutdown, the image with the good driver was as bad as with a bad driver, so that it was impossible to know that the driver is good.
As you have an Asus, the first driver to test is the "ms", then the "a" and "sim".

You just have to run "./pregen503" and answer one or two questions to install the driver.

Thanks for trying.

---

### Post by blazercist on 2008-06-10
Still no joy.... ./pregen* makes it much easier and faster to install the drivers but none of them work for me :(

Cheese just shows me static, camorama freezes and xawtv just shows black....

Thanks for trying to help and thanks for all the work you've done on the driver.

---

### Post by malath on 2008-06-11
hello every one.

i need help regarding my webcam. i have a microsoft usb webcam. it was working just fine on windows, but on ubuntu, nothing appears when i plug the usb cable. when i run the removable drivers and media it say no camera is connected. 

lsusb gives:
Bus 005 Device 003: ID 045e:00f8 Microsoft Corp.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
can some one help please.

---

### Post by Jack Malmostoso on 2008-06-11
> **malath said:**
> 
Bus 005 Device 003: ID 045e:00f8 Microsoft Corp.


According to this mailing list message:

[http://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/002069.html](http://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/002069.html)

Your webcam is a UVC compliant device, therefore the linux-uvc project is your friend.
This page details the Ubuntu specifics:

[https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

---

### Post by nol_faich on 2008-06-11
Hi Blazercist,

sorry for you. So, the 0503 needs at least four drivers. If you have the possibility to install temporarly a windows or know someone with the same laptop and windows, do not hesitate to make logs.

---

### Post by fret_saw on 2008-06-11
Hello, I also have Asus C90s, but with Gentoo linux on it.
I've just tried all 3 drivers from SourceForge, but none of them worked. 
I've got Windows XP installed on VirtualBox, will it be OK to capture the logs, or should I install Windows directly on laptop?

---

### Post by nol_faich on 2008-06-11
Hello, the only one person who tries to make log with Virtualbox failed because USBSniff did not find the webcam. Can you try to confirm ?
If it doesn't work and you can install Windows directly on the laptop, it will be great! We will have the stuff to make the fourth 0503 driver and, we can dream, the last one for that webcam.
Thanks for joining us.

---

### Post by Jack Malmostoso on 2008-06-11
This article might be the reason why I cannot access USB from Virtualbox:

[http://maketecheasier.com/enabling-usb-support-for-vmware-server-in-hardy-heron/2008/05/05](http://maketecheasier.com/enabling-usb-support-for-vmware-server-in-hardy-heron/2008/05/05)

Please give it a try, I'll do it tonight.

---

### Post by fret_saw on 2008-06-11
I couldn't run the tests in VirtualBox either because of this program, or because of the customized Windows distribution installed there ([[COLOR="Blue"]zvercd.com[/COLOR]]("http://www.zvercd.com")). So, I installed the vanilla Windows XP SP2 on laptop and followed the procedure described by Jack. Hope, I understood it the right way. The logs are [[COLOR="Blue"]here[/COLOR]]("http://rapidshare.com/files/121719478/logs.tar.bz2.html").
Thank you very much for what you are doing.

---

### Post by nol_faich on 2008-06-11
Thanks for the logs. There's only two logs with data, the enable and disable ones. In the other there is absolutly no instructions sent by the driver to the webcam. The is such a situation with a 0503 in a Medion laptop. Are you allow to have greater size than 640x480?

---

### Post by nol_faich on 2008-06-11
Here's a new "a" version. It seems to be very near from the original "a" and since I have no answer about if thr previous "a" works, we can dream that the previous "a" was bad and that 3 different drivers are sufficient.

[http://rapidshare.com/files/121729761/gl860-dev-0503a.c.html](http://rapidshare.com/files/121729761/gl860-dev-0503a.c.html)
I hope it works :).

---

### Post by fret_saw on 2008-06-11
Maybe, I've done something wrong while capturing. 
Could you tell, please, if I should capture logs at the moment of changing some setting, or when the state of the device is fixed, i.e. if the procedure should be the following: 
start logging -> run webcam app -> change property -> wait 5 seconds -> kill webcam app -> stop logging, 
or this: 
run webcam app -> change property -> logging on -> wait 5 seconds -> logging off -> change property again -> log again & so on? 
The logs I posted were captured the second way, maybe this is the reason for instructions missing?

I have tried different resolutions from 160x120 to 1600x1200.

---

### Post by blazercist on 2008-06-11
fret_saw I just want to thank you for taking the time and effort to help since I have the asus c90 i can benefit vicariously through you so any help you can provide to nol is appreciated by me.

---

### Post by nol_faich on 2008-06-11
@ Fret_saw : the first way! When you change a setting, the driver send commands to the webcams and by analyzing the logs, we learned what to send while running linux. As you made the captures after the change, there's no more that kind of information.
You can start the capture one second before you change a setting, you will have smaller logs. By the way, for each setting don't forget to give the allowed range of values, the default value, the value you start from and the value you set (eg 0-128, 64, from 64 to 80).

@ Blazercist and Fret_saw : have you try the new "a" version ?

---

### Post by malath on 2008-06-11
> **Jack Malmostoso said:**
> According to this mailing list message:

[http://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/002069.html](http://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/002069.html)

Your webcam is a UVC compliant device, therefore the linux-uvc project is your friend.
This page details the Ubuntu specifics:

[https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)
i tried this project, unfortunately nothing worked up.
isn't there an alternatives?

---

### Post by nol_faich on 2008-06-11
If you are UVC compliant, the svn will not work as your model is not in the list of supported hardware. Change in the line 1802 of uvc_driver.c from "0x0505" to "0xf192".

---

### Post by fret_saw on 2008-06-12
Nol, the latest "a"-driver didn't work also, unfortunately. Should I post here the dmesg or some other logs?

I will capture the logs in Windows again taking into account the information you given as soon as I can.

---

### Post by nol_faich on 2008-06-12
What a shame. Have you shut down your computer after the installation of the new module ? It is mandatory.
I have to modify the text in pregen503 because the restart is needed when the last tried driver does not work, once it works, it no more useful to restart.

If the new "a" version works or not, could you make besides the other captures two logs once again :
- one with the start of viewer, some seconds, and the end of the viewer.
- one with the activation of the device in the windows device manager.

---

### Post by blazercist on 2008-06-12
will try the new "a" version after work today and let you know.

---

### Post by nol_faich on 2008-06-12
The "a" version outside the tarball must replace the one in the tarball ! So just download the "a" version and compile the new driver.

---

### Post by nol_faich on 2008-06-13
New release at SF, it takes into account the different supported image size by the various 0503. The 4 driver flavors are proposed with a new installer (./install).

---

### Post by Jan Olieboer on 2008-06-13
Hi Nol,

Tried the latest driver for my Asus C90S, installed the b-version, but with little success I'm afraid. I still get a lot of errors in my syslog:

gl860: Genesys USB2.0 webcam driver startup
gl860: Genesys USB2.0 - GL860 based webcam found.
gl860: Genesys USB2.0 1.3M WebCam - Product ID 0x0503.
gl860: Release: 0103
gl860: Number of interfaces : 1
gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0030 lg3]
gl860: short ctrl transfer -110/3
gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0034 lg3]
....
gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
usbcore: registered new interface driver usb_gl860_driver
gl860: v0.3.0 : Genesys gl860 USB Video Camera
gl860: Demande de la taille 640x480
gl860: ctrl transfer failed -110 [p40 r1 v0003 i00c1 lg0]
...
gl860: short ctrl transfer -110/3
gl860: Gestion de l'erreur 45
...

Wish I knew why there are so many different versions required. Noticed in the Windows driver that that driver is prepared to take 2 backends, i.e. one for an OmniVision OV2640 optical chip, and one for a Micron MI2020. I'm using Ubuntu 8.04.

Cheers,
Jan.

---

### Post by blazercist on 2008-06-13
> **Jan Olieboer said:**
> Hi Nol,

Tried the latest driver for my Asus C90S, installed the b-version, but with little success I'm afraid. I still get a lot of errors in my syslog:

gl860: Genesys USB2.0 webcam driver startup
gl860: Genesys USB2.0 - GL860 based webcam found.
gl860: Genesys USB2.0 1.3M WebCam - Product ID 0x0503.
gl860: Release: 0103
gl860: Number of interfaces : 1
gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0030 lg3]
gl860: short ctrl transfer -110/3
gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0034 lg3]
....
gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
usbcore: registered new interface driver usb_gl860_driver
gl860: v0.3.0 : Genesys gl860 USB Video Camera
gl860: Demande de la taille 640x480
gl860: ctrl transfer failed -110 [p40 r1 v0003 i00c1 lg0]
...
gl860: short ctrl transfer -110/3
gl860: Gestion de l'erreur 45
...

Wish I knew why there are so many different versions required. Noticed in the Windows driver that that driver is prepared to take 2 backends, i.e. one for an OmniVision OV2640 optical chip, and one for a Micron MI2020. I'm using Ubuntu 8.04.

Cheers,
Jan.

I saw some of these same errors on boot with the older driver installed as well.  I'm having problems unrelated to the driver which are preventing me from testing further, but I will test further once its cleared up.

---

### Post by nol_faich on 2008-06-13
I made a mistake with one of the two instructions to stop the webcam as that one is not like the one of the "a" version. As xawtv and some other viewers restart the webcam several times before we have a picture, maybe that bad halt causes trouble. Sorry for that.
Please try the 0.2d release. Otherwise, the source code matches the Fret_saw's logs. If the new release does not work, I need new logs with initialisation and video stream (start of viewer, some seconds and halt of the viewer) to compare to the previous ones.
[https://sourceforge.net/project/showfiles.php?group_id=229562]("https://sourceforge.net/project/showfiles.php?group_id=229562")

@ Jan : I don't know. These two chips are 2MP and one of the 0503 seems not able to do more than 1280x960. And I don't know how to distinguish among the different models the one you have. With the original driver, the author had an image, someone else a scrambled image which look like nothing and a third one not any single byte sent by the webcam. Maybe it will be possible to distinguish between the "a" and "b" if one of these two flavor is to use.

---

### Post by blazercist on 2008-06-13
It doesn't work for me, the light on the camera doesn't even turn on now.

EDIT: OMG!!!!!! I tried to open camorama and as usual it hanged so i left, when i came back THERE IT WAS!!! a black and white image of my refrigerator, camorama is frozen, but finally i have an image!!!!  its upside down too...

i am using the newest "b" driver


I keep trying but i cannot reproduce this....

---

### Post by cacycleworks on 2008-06-14
I have spare winXP (or vista) cds if anyone would wish to borrow them. 

I'm also posting to this thread as I have previously tried to make a webcam work in linux without success. This thread has more info in 10 posts than 10 hours of my google searching. A possible future prospect for business involves needing a webcam that I can broadcast, and thinking of going back to windows gives me stomach aches.

Thanks to all of you for this effort! 

:-) Chris

---

### Post by nol_faich on 2008-06-14
Maybe there is something wrong at the end of the driver so that you need to restart your computer to have once again a picture.

Don't try to make something with 320x240, just use "camorama", without paramaters, it should work.
Could you add these four lines in "base_gl860.h" from the line 122 :

#undef CONFIG_GL860_DEBUG_STREAM
#define CONFIG_GL860_DEBUG_STREAM 1
#undef CONFIG_GL860_DEBUG
#define CONFIG_GL860_DEBUG 1

They will enable the debugging and let a lot of traces.
I need the result of "grep gl860 /var/log/syslog" to try to understand why you freeze and why this is long you to have a picture with camorama. So add the lines, use ./install, launch camorama, wait until you have something and you see it is frozen and stop camorama. Post or upload the txt file resulting from "grep gl860 /var/log/syslog > traces.txt".

---

### Post by blazercist on 2008-06-14
ok so i added those lines and tried some more, this time i managed to get a moving image and camorama didn't freeze, but the image was screwed up, i couldnt really see anything but i kno it was working because when i moved my hand it changed....

the problem is that traces.txt is almost 500Mb lol, 

it hasnt finished loading, i dont think it ever will, its filled with this:

Jun 14 14:57:15 geoff-laptop kernel: [  517.459953] gl860: URB : Length = 2 - Skip = 2 - Buffer size = 0
Jun 14 14:57:15 geoff-laptop kernel: [  517.459955] gl860: URB : Length = 2 - Skip = 2 - Buffer size = 0
Jun 14 14:57:15 geoff-laptop kernel: [  517.459957] gl860: URB : Length = 2 - Skip = 2 - Buffer size = 0
Jun 14 14:57:15 geoff-laptop kernel: [  517.459959] gl860: URB : Length = 2 - Skr0000: URB : Length = 2 - Skip = 2 - Buffer size = 0
Jun 14 14:57:15 geoff-laptop kernel: [  517.461263] gl860: URB : Length = 2 - Skip = 2 - Buffer size = 0
Jun 14 14:57:15 geoff-laptop kernel: [  517.461264] gl860: URB : Length = 2 - Skip = 2 - Buffer size = 0
Jun 14 14:57:15 geoff-laptop kernel: [  517.461266] gl860: URB : Length = 2 - Skip = 2 - Buffer size = 0
Jun 14 14:57:15 geoff-laptop kernel: [  517.461268] gl860: URB : Length = 2 - Skip r0000: URB : Length = 2 - Skip = 2 - Buffer size = 0
Jun 14 14:57:15 geoff-laptop kernel: [  517.462571] gl860: URB : Length = 2 - Skip = 2 - Buffer size = 0
Jun 14 14:57:15 geoff-laptop kernel: [  517.462573] gl860: URB : Length = 2 - Skip = 2 - Buffer size = 0

thats tail from traces.txt, ill keep trying to open traces.txt and get the last 1000 lines or so.

i tried with camorama -M just now, and after several failures and alot of waiting i got a moving picture that makes sense!!! its a little screwed up but proves that you are moving in the right direction!

also its very weird but the camera is WAY off center, if i sit directly infront of it  it doesnt see me i have to sit to the left of the laptop and then it sees me... weird...

heres tail from /var/log/syslog when camorama doesn't freeze

Jun 14 15:20:03 geoff-laptop kernel: [ 1413.192274] gl860: URB : Length = 850 - Skip = 2 - Buffer size = 115408
Jun 14 15:20:03 geoff-laptop kernel: [ 1413.192276] gl860: URB : Length = 1074 - Skip = 2 - Buffer size = 116480
Jun 14 15:20:03 geoff-laptop kernel: [ 1413.192278] gl860: URB : Length = 642 - Skip = 2 - Buffer size = 117120
Jun 14 15:20:03 geoff-laptop kernel: [ 1413.192280] gl860: URB : Length = 642 - Skip = 2 - Buffer size = 117760
Jun 14 15:20:03 geoff-laptop kernel: [ 1413.192283] gl860: URB : Length = 642 - Skip = 2 - Buffer size = 118400
Jun 14 15:20:03 geoff-laptop kernel: [ 1413.192285] gl860: URB : L413.192296] gl860: URB : Length = 851 - Skip = 2 - Buffer size = 123089
Jun 14 15:20:03 geoff-laptop kernel: [ 1413.192299] gl860: URB : Length = 1073 - Skip = 2 - Buffer size = 124160
Jun 14 15:20:03 geoff-laptop kernel: [ 1413.192301] gl860: URB : Length = 642 - Skip = 2 - Buffer size = 124800
Jun 14 15:20:03 geoff-laptop kernel: [ 1413.192303] gl860: URB : Length = 642 - Skip = 2 - Buffer size = 125440
Jun 14 15:20:03 geoff-laptop kernel: [ 1413.192305] gl860: URB : Length = 642 - Skip = 2 - Buffer size = 126080


as you can see the only difference seems to be the buffer size which i dont kno anything about programming so i don't know what that means :)

OK lol, i've edited this post about 25 times already, i realize that im an idiot, "tail -n 500 traces.txt > tracing.txt" only problem is that i cant attach it because its over 19.5Kb, so if you like i email you.

---

### Post by nol_faich on 2008-06-15
@ Blazercist
OK, what is interesting is the beginning of the traces if camorama did not freeze. The first 1000 lines will be sufficient to see what happens at the beginning. If the characteristics of the images change, it is that the webcam don't really understand what i send, there is a random part in the behaviour of the webcam. Someone else has images as your last one, but I have no logs.
My email is given in the first lines of relog.c .

@ every body with a windows : a new "relog.c" is at SourceForge, I add a new information when tracing.

---

### Post by nol_faich on 2008-06-15
I still made a little change in "503b", the end of the initialization sequence issued from Fret_saw logs is weird compared to the one of the other flavour. I changed it. So please try with the 503b outside the tarball.

---

### Post by blazercist on 2008-06-15
no change with the new "b" , after a long wait and several failed attempts i got a garbled image that moved and the logs are almost the same...

---

### Post by nol_faich on 2008-06-15
We have to wait for new logs...
I hope to have soon logs from an Asus S37S. Maybe it will be from the same driver branch as C90.

---

### Post by nol_faich on 2008-06-15
@ Olieboer : my 05e3:f191 uses a MI1320. You must be right about the diversity of drivers.

@ all with the Windows driver : could you send your gl860.inf? There is interesting informations about capabilities and data to send for the settings.

Use &#8220;Submit new&#8221; of the &#8220;Request for supports&#8221; in SF ([https://sourceforge.net/tracker/?group_id=229562&atid=1077409](https://sourceforge.net/tracker/?group_id=229562&atid=1077409)) to upload the file.

---

### Post by nol_faich on 2008-06-17
Asus C90s driver seems to be very similar to the one for Asus S37S which is also similar to the original driver by Daniel Drake. There is some differences but I think you can test the last release at SF. Try the "a" flavor.

---

### Post by blazercist on 2008-06-17
someone posted in reply to a thread i started with the C90 driver here is the thread [http://ubuntuforums.org/showthread.php?t=831167](http://ubuntuforums.org/showthread.php?t=831167)

that said, as always I will test the new release after work today.  hopefully my internet at my house will be working again.

@nol:  so the C90 people like myself should now try "a" instead of "b" ?

@myself: I check this thread WAY too often. :)

---

### Post by nol_faich on 2008-06-17
Thanks for the gl860.inf. Don't try the online driver !
The C90S have the same chip as mine but with little difference, I make a version for you.

---

### Post by blazercist on 2008-06-17
you are the most awesome of awesome

---

### Post by nol_faich on 2008-06-17
The files are online. Just download the two files outside the tarball (install and the 503blz) and run ./install
As we have some different features, I hope that the main part of the driver is the same.
Good luck !

---

### Post by blazercist on 2008-06-17
ok, good and bad, i just installed and now camorama doesn't take 5 minutes to load, it now opens up right away :) but it still freezes... i did grep gl860 /var/sys/syslog > traces.txt and now it looks completely different. so im attaching the file.

The computer doesn't hang at boot which is great

i rebooted the computer after install and im going to try to run camorama and just leave it to see if it unfreezes...

---

### Post by tricid on 2008-06-18
I have an asus c90, and the same problems described above (freezes, hangs, etc)

The good news, I also dual boot XP. If this is still being actively worked on, let me know and I will provide you with whatever logs/sniffs you need. I would love to see this webcam work myself.

- Rick

---

### Post by blazercist on 2008-06-18
@ tricid : if you look at earlier posts in this thread it describes the procedure for USBsniff logging, also you could send a copy of your gl860.inf along with any logs you have...

also, you could try the newest driver "0503blz" and post the output of ```
 grep gl860 /var/sys/syslog > traces.txt 
```

---

### Post by tricid on 2008-06-18
Here is my traces file.

Some notes:

the blz version, my system still hangs, but its not as long of a hang as with the other versions. 

Camorama opens in a frozen state now. Other versions it would freeze before a window would even open. Now it opens, and freezes before its own window finishes loading, or loads the image box with blueish fuzz then freezes.

I'll reboot now and work on getting some usb sniffer logs.

---

### Post by blazercist on 2008-06-18
exact same behavior as mine so at least i kno im not doing something wrong, does the camera light go on for a few seconds, then off, then on again?

---

### Post by tricid on 2008-06-18
Sounds the same as me.

When I boot, it'll hang a bit and flash a couple times, maybe a minute or two at the most (other drivers could be as much as a 5 minute hang), then continue. 

When I open kde, it'll blink a few times then stops.

Then when I open camorama, it'll blink a few times, pause, finally camorama opens but the UI doesn't fully load most of the time, then the light will be on solid.

I'm on XP now, working on getting some logs sniffed

---

### Post by tricid on 2008-06-18
Not to sound foolish or anything, but usb sniffer wont let me start any sniffing. The log area, most of the buttons are greyed out. I've installed the sniffer for the cam, while the cam is disabled, per the instructions earlier in the thread.

Attached is my inf file, but it was located in WINDOWS/temp, not sure if that's normal, maybe because I currently  have it disabled?

---

### Post by nol_faich on 2008-06-18
What is your laptop ?
For the logs, try to make logs while viewing images and logs while changing one parameter.

---

### Post by nol_faich on 2008-06-18
Your logs say that the webcam does not understand anything. Either the gl860.inf I got from a C90s in another thread is not good, either you have no chance with a same gl860 and sensor as me but a totally different driver. I prefer to think the gl860.inf is bad. So you are from the original branch of the driver.

The 0503 is a quite strange device.

The logs of Fret_saw are very near from the "a" version while a GL860.inf said that it is the same chip as me with a f191 and so another driver. It is going to be crazy.

Actually, for the gl860 there's :
* one full supported f191, chip MI1320 (sizes and settings)
* one full supported 0503 for Asus Z37E, chip OV2640 (sizes and settings OK)
* one partially supported 0503 for Medion laptops, chip OV9655 (brightness and 640x480 - 1280x960)

Both other not supported are from the same driver branch but it is unclear what chip it is and if there is really différences between both drivers to do. The initialization sequence is the same, but some traffic which seems to be a setting, not commands. The instructions for left-right inversion, brightness and sharpness are the same. The only real difference is traffic which does not look like settings for your model and the two stop commands sent to webcam.

I hope logs will help me to understand what is commands and what is settings.

---

### Post by blazercist on 2008-06-18
nol i dont want to confuse you, i think i said it in the original post but that gl860 that I posted is not mine, I started a thread asking for help from anyone who had an asus c90, it is possible that the guy who posted his driver misunderstood.

it seems that tricid actually has the C90 and windows XP so perhaps his gl860 is the right one to look at.

that said I'd like to thank you nol for all the work you've done.

---

### Post by tricid on 2008-06-18
Attached is a usbsniffer log from opening my camera. I had to cut a good bit out for size, but I think I included everything from it opening, and maybe even a few sections of it transferring. Let me know if this is sufficient.

---

### Post by Jack Malmostoso on 2008-06-18
Nol, AFAIR the nice people at System76 are selling laptops with gl860 based webcams. Maybe you could post over there and see if they can help?
If they are actually selling those devices, they will sure as hell be interested in a driver.

Here's the link to their forums:

[http://ubuntuforums.org/forumdisplay.php?f=158](http://ubuntuforums.org/forumdisplay.php?f=158)

---

### Post by nol_faich on 2008-06-18
I understood that is was not your gl860.inf and that is why i prefer to forget it. 
I have some logs from a Asus S37S, chip MI2020, however it has less allowed settings than the Asus C90s, chip MI2020. This could explain most of the traffic differences. So logs from Tricid will be very important to progress.
I am trying to understand what could be a setting or not.

---

### Post by tricid on 2008-06-18
To find that inf, I just searched my system for "gl860.inf". It's only result was a file in Windows\Temp, which seems odd to me.  I'm not even sure if this is the correct INF to be honest, it's just the name of the one you linked earlier I believe, so I searched for the same name on my computer.

If my computer is using a different inf file, how can I poke around to find out what it's using?

It just seems an odd location for it if it is the one my computer is actually using to access my webcam.

If thats normal please let me know, I'm a windows noob

---

### Post by nol_faich on 2008-06-18
Tricid, please compile "relog.c" in the tarball and post the ".c" resulting from "relog a_log_file tri". Your log missed data. And if you can, log with one varying setting are important.

I was told yesterday about System76. I will see but one reports me it could be proprietary driver. It is unclear.

I have Vista and my location is "Windows/System32/DriverStore/FileRepository/gl860.inf_f64698ba", I have no idea for XP.


There is driver to download at [http://planet76.com/repositories/](http://planet76.com/repositories/). I try

I am browsing their sources. They speak about uvc, which is a standard for webcam, however our dear "gl860" does not comply with uvc, on contrary to the gl860a. I go further  and i need logs !

At first sight, there is nothing for the 0503, there is drivers for uvc and gspa. :( It could explain why Daniel drake tried to make a driver...

---

### Post by blazercist on 2008-06-18
neither of the laptops on system76.com seem to be the C90, i will try anyway when I get home.

---

### Post by tricid on 2008-06-18
Here's the inf from the driver download itself. I glanced at it, it looks the same (but a different version). 

Not sure if it'll help, just trying to be thorough

---

### Post by blazercist on 2008-06-18
the most important thing right now i think are the logs... if you can make as many detailed usbsniff logs as possible then i think nol will have something to work with.

like it says just change one setting at a time mark each file accordingly and save it.

---

### Post by tricid on 2008-06-18
I'm sorry I missed data, I'm not sure how much you need so I just cut out some of the beginning and sent it.

With only 5 seconds of capturing the log file was around 61 megs.

I can send it that big if you know of a place I can upload it to, and if you need all of it. 

You confused me with the recompiling part, do you mean get back on linux and do that from your driver? Or is that something I'm supposed to do one windows?

Sorry if I'm slow lol

---

### Post by tricid on 2008-06-18
I'll make them as long and detailed as you need with any setting changes you need, I'm just not sure how big you need them to be. Like I said, 5 seconds was over 60 megs. I don't know where I can upload a file that big, unless I can send to you direct (aim, irc, msn, etc)

---

### Post by blazercist on 2008-06-18
the logs shouldnt be that big, the relog.c file that is included with the driver is (from my underestanding) intended to be applied to the raw log files in order to filter them and cut them down to a managable size.

>  Put the logs and relog.c in a directory. Compile relog.c
Code:

$ g++ relog.c -o relog

and you'll obtain an executable named relog. Assuming that all logs you took have the extension .log, just type this to have them all automagically processed
Code:

$ cd /directory/with/logs/and/relog
$ for i in $(ls ¦ grep .log); do ./relog $i msc; done

You'll end up with a bunch of .bmp images, a bunch of $i.loglog files and the most important ones, $i.c files. These are the files that are *really* needed to create the driver. Pack them up (make sure they have representative names and include a README file with some additional explanation if needed) and make them available to Nol 

---

### Post by nol_faich on 2008-06-18
From the system76 forum, i saw that not all webcam are supported. Now it is clear.

I compile a relog.c for windows xp

---

### Post by tricid on 2008-06-18
oh ok, I understand now.

I'll do all the logs, changing various settings, then reboot and compile/run that against them on linux. 

I'll try to do that before I leave work, hopefully you'll see something soon.

---

### Post by nol_faich on 2008-06-18
just compile relog.c once, if you can compile on windows, make it ! it makes only use of standard libraries.

---

### Post by tricid on 2008-06-18
If you could compile one for windows XP for me, that would be great. I could do that right now. 

I just took two logs. I opened the cam, left it for a few, then closed the cam. Waited for the logs to catch up with their writing, then paused and saved.

I changed the brightness from 70 to 60, then did the same thing. So now I have two logs waiting to run your filter on them.

Let me know if that process will get you what you need, or if you need the logs active while I actually make the change.

---

### Post by nol_faich on 2008-06-18
Here is the relog.exe (command line tool!). I hope it works.

---

### Post by tricid on 2008-06-18
Attached are 3 logs.

60HZto50HZto60HZ.txt.c.gz

Opened cam, changed power to 50Hz, then back to 60Hz, then closed cam.


open-close-brightness60.txt.c.gz

Opened cam, ran a few seconds with brightness on 60, closed



open-close-brightness70.txt.c.gz

Opened cam, ran a few seconds with brightness on 70, closed




Let me know if this helps.

---

### Post by tricid on 2008-06-18
Also, all the bmp's produced were upside down.  Not sure if that's important

---

### Post by nol_faich on 2008-06-18
Please change several times the parameter you are logging, it is to be sure what i get is ok. For the brightness, it is the same as the "a" version. I have a new information with 50/60 Hz. I'm impatient to have the other logs !

Your logs Tricid are amazing, this is exactly the initialization sequence of the "a" flavor with one of the "b" changes. So if you have a C90S, you are closer to the Asus S37S than the C90S of Fret_saw.

---

### Post by cacycleworks on 2008-06-18
This is embedded software engineering at its finest!! Makes me miss a previous job... 

Thank you all. This is better than almost any sport on TV! Maybe SBK and MotoGP are better. :)

Thanks,
Chris

---

### Post by tricid on 2008-06-18
Attached file contains logs and README



README is as follows, just so everyone knows what it contains without downloading.

_________________________________________________________________


Default frame rate: 30FPS

Default resolution: 640x480



AC Power Frequency

50Hz or 60Hz settings using radio buttons. 

Each chosen several times, starting and ending with 60Hz



Backlight Comp

0 - 64 Min - Max settings using slider. Default 0 (I think)

Moved up and down to both maxes several times, then put back to default.



Brightness

0 - 128  Min - Max settings using slider.  Default 70.

Moved up and down to both maxes several times, then put back to the default.



Contrast

0 - 3 Min - Max settings using slider. Default 0.

Moved up and down to both maxes several times, then put back to default.



Gamma

0 - 2 Min - Max settings using slider. Default 0

Moved up and down to both maxes several times, then put back to default.



Hue

0 - 200 Min - Max settings using slider. Default 0.

Moved up and down to both maxes several times, then put back to default.



Saturation

0 - 100 Min - Max settings using slider. Default 60

Moved up and down to both maxes several times, then put back to default.



Sharpness

0 - 40 Min - Max settings using slider. Default 20

Moved up and down to both maxes several times, then put back to default.



White Balance

0 - 100 Min - Max settings using slider. Default 50

Moved up and down to both maxes several times, then put back to default.



Notes:

There were other options, but they were things like face tracking, special effects, etc that I figure 
is probably software controlled, so I didn't bother logging them. 

_________________________________________________________________

Let me know if anything is needed that could be of help.

---

### Post by tricid on 2008-06-18
Oh, there's also a flip (vert and horiz) option, I didn't log those. Let me know if that's needed.

And before I forget, thank you very much for your efforts. Whether you get this working or not, or anything in between, your efforts are greatly appreciated.

---

### Post by tricid on 2008-06-18
blazercist:

It's not on the subject of the webcam, so I apologize if this isn't ok for this thread, but...

Have you heard/seen any news as far as the over clocking features of this laptop being enabled in linux (TurboGear?)?

Other than the webcam, that's the only feature I'm really wishing I had in linux.

---

### Post by blazercist on 2008-06-18
tricid, no sorry i haven't gotten to that point yet with this lappy, i dont think its necessary this thing is pretty fast as it is...

---

### Post by tricid on 2008-06-18
Yes, it is plenty fast as is, was just curious lol

I'd rather have the webcam working anyway :D

---

### Post by nol_faich on 2008-06-19
I also need the flip options. and you are right, face tracking and likes are not managed by the driver. With my webcam you although have a flip managed by the driver and another one by the viewer! all the options are sent after the commands to ask the webcam to take picture, so the flip options are still some traffic to understand. I will look at the file in 4h.

---

### Post by tricid on 2008-06-19
Were the logs I sent good enough for the options I covered?  I'll log the flip options today, along with different resolutions.

Let me know when you have a driver you need me to test, and thanks again for your hard work :)

---

### Post by tricid on 2008-06-19
More logs


README:

Flip - Checkbox

Flipped the image 5 times, starting and stopping at it's default setting.



Mirror - Checkbox

Mirrored the image 5 times, starting and stopping at it's default setting



Resolution 1600x1200  (was very choppy, and the relog output hinted that it had problems 
staying at this resolution, sometimes outputting 640x1200 images, or odd numbers like 1600x1171)

Switched back and forth 2 times, starting and stopping at the default 640x480.



Resolution 1280x1024  (stayed pretty smooth from here on)

Switched back and forth 2 times, starting and stopping at the default 640x480.



Resolution 800x600  

Switched back and forth 2 times, starting and stopping at the default 640x480.



Resolution 352x288  

Switched back and forth 2 times, starting and stopping at the default 640x480.



Resolution 320x240  

Switched back and forth 2 times, starting and stopping at the default 640x480.



Notes:

I noticed anything lower than 640x480, relog stops outputting different sized bmp's, 
they all stay 640x480.   I assumed this to mean it's no longer making calls to the hardware for the
lower resolutions, so I only went two steps below that.  If this is incorrect let me know and I'll log the rest.

---

### Post by tricid on 2008-06-19
The only settings left are:

Special effects and face tracking, which we already discussed, that's all software.

There's a light source setting, low light, normal light, backlight.   Let me know if I should log those, I wasn't sure.

There is a color space option with three settings: YUY2 (default), RGB24,  I420.  If you want me to log those let me know. 

Then there are FPS settings that are grey to me (default 30FPS), and quality/compression settings that are also grey.

---

### Post by nol_faich on 2008-06-19
Light source is interesting, try colorspace settings, til yet it has no effect on the webcam but there is so many strange things that it could also be useful.
Saturation, Hue and White Balance are not managed by the webcam, it is a post-image acquisition job.

---

### Post by nol_faich on 2008-06-19
Asus S37S and C90S are definitely almost the same. Same instructions to set parameters and same data sent for choosing the image size.
There is some weird things as some settings appear slightly different when they are change manualy or automaticaly by the driver, I never saw that before. I work on the version with all known settings.

I also add the timecodes in relog. Maybe we have to wait sometimes before sending something to the webcam.

---

### Post by theZoid on 2008-06-19
> **nol_faich said:**
> Asus C90s driver seems to be very similar to the one for Asus S37S which is also similar to the original driver by Daniel Drake. There is some differences but I think you can test the last release at SF. Try the "a" flavor.

C90 here!  Keep up the good work !!!

---

### Post by nol_faich on 2008-06-19
New release at SF.
For Asus c90s, it is the "b" version.
I will be surprised that it works as most of the work was to add settings and study the difference with the "a" version. Both versions are now merged in one file.
I need new logs of "viewer launch + some images + viewer halt" with the NEW relog in the tarball.

---

### Post by tricid on 2008-06-19
New version doesn't initialize the cam, the light never comes on and camorama never opens.

I'll do some new logs with the new relog tonight or in the morning :)

---

### Post by hulkie on 2008-06-20
Hello everybody,

I also have a 05e3:0503 Genesys Logic webcam in my Z37sp laptop, so I am very excited to see that work is underway on a driver. Not having a dual boot, I was hesitant to install windows to generate the logs, but IT WORKS WITH VMWARE PLAYER! (the virtual windowsXP was taken from a genuine windows install with vmware converter) SniffUsb detects the webcam and using the program Yawcam, I can see myself smiling in the webcam. Some logs are created. Next week I won't be able to create logs as I have too much work, but after that, I will be able generate plenty of log files.

Looking forward to it.
Sam.

---

### Post by Jack Malmostoso on 2008-06-20
Hulkie, that is awesome news! Did you do any particular setup in Vmware or did it work out of the box?
It could be interesting for others that don't have a dual boot.

Speaking of which, I can remove mine, now :D

---

### Post by hulkie on 2008-06-20
Well, here I am again,

I couldn't resist making those logs straight away. I attached them. The explication of what I did is in the name. For most actions (like flip), I started from normal - pressed flip and stopt logging. Reversing from flipped to normal was done in another logging session. For changing formats (resolution and colour space) the webcam started up with the default, so I could not isolate the commands.

I couldn't upload the loglog and bitmap files as they are too big, Should I mail them directly or do you have enough already?

Hope this helps in the development.
Good luck!
Sam.

---

### Post by hulkie on 2008-06-20
No I didn't do anything special in vmware player. The webcam shows up as an available usb-device in the vmware player. You select it and then it is available in the windows client. And logging works. Indeed, I hope that this will increase the amount of logging files.

Ps: for the model of my webcam, I have a 'generic' laptop (no indication of asus or medion), I bought it from Priminfo, a small company in Belgium and they sell it as the Priminfo Z37sp..

---

### Post by tricid on 2008-06-20
Something similar is possible with virtualbox (non-free version), but last time I checked the usb code had some bugs that wouldn't let the cam actually work (any cam). I think it had something to do with bandwidth over usb, I can't recall. This is also speaking about something that I haven't tried in a few months now, so who knows.

I may try virtualbox later just to see if there has been any improvement there.

I've used usb devices on VMware and virtualbox both for a while now though, so I wasn't sure why people were saying their cams won't work (other than said bug concerning virtualbox's usb stack, if it still exists)

---

### Post by blazercist on 2008-06-20
So the cam actually works in vmware?  I could use it to chat in a virtual machine?  Perhaps, for now, I will install vmware and a virtual windows box if I can find a cd.

---

### Post by tricid on 2008-06-20
I'm pretty sure I have used vmware for that very purpose on this laptop, then later stopped when I switched to virtualbox and it had that bug and I didn't feel like redoing VMware again. They both do have USB 'passthrough' options of some sort.

I do apologize if this is incorrect, my memory isn't always the best lol

---

### Post by nol_faich on 2008-06-20
Welcome Hulkie!

Your webcam is the same as Fret_saw, so the "b" flavor. Your logs with swtich to lowlight, backlight and normal light are interesting because i still don't have these however you have to wait some seconds before making the switch because it seems that the switches are to search in the other settings or command traffic instead of being alone among the video stream.
There is some part where there is 0,05s between two instructions sen to the webcam which is more than the usual delay. I will try to add that delay in the driver.

---

### Post by nol_faich on 2008-06-20
New release at SF.

I fix a bug in the initialization sequence that is not exactly the same with "a" and "b". I also add delay before or after some commands to  respect what is done with Windows.

I Hope it is better

---

### Post by tricid on 2008-06-20
I think we've gone backwards someplace, it won't even cause the led to turn on my cam anymore

---

### Post by nol_faich on 2008-06-21
OK Tricid. You was more "a" than "b" but if it is so bad, I add a third flavor, the "c" for you at SF (v0.2h2).

Blazercist : likely "b" or "c"
Fret_saw and Hulkie : "b"
Tricid : "c"

If with camorama you have nothing, I would like to have "grep gl860 /var/log/syslog".

@ Fret_saw and Hulkie : I need logs when you are in 800x600, 1280x960 and 1600x1200.

@ all : I need log with change from normal light source to low, normal to back and back (or low) to normal. The change must be made 5 seconds after an image is in the viewer.

---

### Post by theZoid on 2008-06-21
> **tricid said:**
> Were the logs I sent good enough for the options I covered?  I'll log the flip options today, along with different resolutions.

Let me know when you have a driver you need me to test, and thanks again for your hard work :)

Thanks from me too!  Many are watching and waiting that aren't posting much, like me....I wish I could help.

---

### Post by tricid on 2008-06-22
Sourceforge (or my computer) seems to be messing up, I can't download any files. I click the release, then no files show up downloadable.

I'll keep trying, could just be a fluke. After I get them I'll test the "c" version and let you know.

I'll also create more logs this weekend of the light source changes. I'll give decent delays in between commands to try and filter them out of normal traffic a little better, my apologies for that.

---

### Post by tricid on 2008-06-22
Also I'm kind of curious why mine seems to be so different, was fret_saw also on an asus c90?  Did these laptops have different revisions of the webcam maybe?  Is there a way to check?

Mine was probably in the first few batches of released c90s, maybe fret_saw's is a more recently purchased one with slightly different hardware?

---

### Post by tricid on 2008-06-22
Excellent.

I was finally able to download (h3), and my cam works using the "c" option.

It initializes (slowly), then camorama or cheese opens and I can see myself.

I'm upside down and none of the color/contrast/brightness settings seem to have any effect, but it opened without any problems other than slowness. The frame rate was also awful, but that may be camorama/cheese's fault, I didn't see an option to change the frame rate.

To be fair though, at times, on windows it's slow to open too. We're only talking 3-5 seconds here. 

Excellent work, you're making great progress!

---

### Post by blazercist on 2008-06-22
YEY me too, It was same behavior like tricid, it opens slowly and then i can see me but its upside down!  brightness, white balance and hue work for me in camorama, contrast does not.

---

### Post by blazercist on 2008-06-22
also, on the right side there is a black bar, like the picture is a little cut off. im not sure if it is supposed to be there but camorama wont let me resize the window.

---

### Post by nol_faich on 2008-06-22
It is a good news. I would like to be sure to understand, with linux your webcam needs 3-5 linux to be ready ?
Color/contrast/whitebalance do not work because it is post processing done by the driver, the webcam does not manage it. I will add the support for basic settings not managed by the webcam. However brightness should work.
I can't tell you much about your webcam because i have no initialization log from you but all such logs i have show exactly the same data, so there is no information about what driver to use or why it is different.
I have three logs for your gl860+sensor. You send exactly the same value triplets to the webcam as Iceman's log (not on this forum) but your commands are exactly the one of Fret_saw but one value changed.
Have you tried xawtv, you can test all settings with it.


@ blazercist : which version do you use ? Could you test the settings with xawtv ? Could you post a picture ?
Camorama does not allow you to use the great size or the small?

@ Tricid and Blazercist : could you verifiy that the picture is only verticaly inverted ? Camorama without argument is defaulted to 800x600 because it uses the max size/2. If you have this size when you launch it, this is maybe due to that. Try Camorama with then command argument to control if it is faster.

---

### Post by blazercist on 2008-06-22
I used "c" version, xawtv also works and is also upside down. if i try to "grab image" with xawtv it freezes and he cam turns off. Its slow to initialize with xawtv also.

If I change a setting in xawtv, the camera freezes the light turns off, then i wait 10-15 seconds and it comes back (sometimes).  the settings dont seem to really affect anything.

---

### Post by nol_faich on 2008-06-23
@ blazercist : The image seems to be "normal", but the real part of the image is 640x600 although i receive as many bytes as if it is 800x600. Maybe still something strange with that cam. Have you tried 640x480 and is it quicker ? Have you tried 1600x1200?
Xawtv is great because it proposes you to set everything i allow in the driver on contrary to others but xawtv is stupid since it restarts the webcam each time you change a setting although it is not useful. It is needed when you change the resolution but not when you want to change a setting.
For testing settings, you try what is explained in README with message sent in command line as echo "value" > /sys/.../setting. Try for example hflip and vflip with "value" = "0" or "1" to control if these settings work.

@ Tricid : have you the same issue with black bar on right? Could you send me pictures generated by relog in 640x480, 800x600, 180x960 and 1600x1200 ? i need to see if it is due to sensor.


Try this script to change settings :

echo -e "1 = hflip yes  [-1 = no]\n2 = vflip yes  [-2 = no]\n3 = size 640x480\n4 = size 800x600\n5 = size 1280x960\n6 = size 1600x1200"
echo "Which number :"
read cmd

if [ "$cmd" = "-1" ]; then
        cd /sys/class/video4linux/video0
        echo 0 > hflip
elif [ "$cmd" = "-2" ]; then
        cd /sys/class/video4linux/video0
        echo 0 > vflip
elif [ "$cmd" = "1" ]; then
        cd /sys/class/video4linux/video0
        echo 1 > hflip
elif [ "$cmd" = "2" ]; then
        cd /sys/class/video4linux/video0
        echo 1 > vflip
elif [ "$cmd" = "3" ]; then
        killall camorama
        camorama camorama -D -R --width=640 --height=480
elif [ "$cmd" = "4" ]; then
   killall camorama
        camorama camorama -D -R --width=800 --height=600
elif [ "$cmd" = "5" ]; then
   killall camorama
        camorama camorama -D -R --width=1280 --height=9600
elif [ "$cmd" = "6" ]; then
   killall camorama
        camorama camorama -D -R --width=1600 --height=1200
fi

---

### Post by blazercist on 2008-06-23
yes the image is "normal" except for my hair :)  Yes, xawtv is weird I didn't realize it restarted the cam everytime i changed a setting maybe that is why it froze up like that.  I haven't tried timing with different resolutions although I have tried camorama -m and camorama -M and just camorama, which if I understand correctly basically does minimum resolution, default resolution and max resolution all initialized slowly and seemed to work fine. just to make sure, is the script for me or tricid?

---

### Post by nol_faich on 2008-06-23
For both of you ! You have the same driver.
It is to control that you have all sizes and that the flip settings are managed. If you have an upside-down image, i have to change that in the 503a's settings function.
For camorama, small and big sizes are defined in the driver and asked by camorama, it is 80x60 and 1600x1200. Camorama uses as "default" the maxsize/2, so 800x600 which is not the very webcam default.
The script is for both of you to verify you have 640x480 and 1280x960 which are not allowed in camorama's GUI without typing by hand :).

I will make a script to test all settings. Now that you have an image, what is important is to confirm that all settings are working i order to have an almost final release for the model.

---

### Post by nol_faich on 2008-06-23
I attached another 503blz. This 503blz is a 0503a without delay between some instructions. Could you compile the "blz" version, shutdown your computer and tell me if it works after restart. It is to know wether the previous drivers were not work because of the absence of these delays.
Once it is done, install the "c" version.
There was also a script to test settings but i overwrote it. I'll redo it later.

I would like also the "grep gl860 /var/log/syslog" obtained from the good driver (503a, not blz).

---

### Post by blazercist on 2008-06-24
I tried that script you posted in post #137, it didn't work for some reason, I have no idea why.

I didn't get a chance to try the new driver yet I will do that today after work.

---

### Post by nol_faich on 2008-06-24
The script to test the webcam. It encompasses some settings you don't have or not managed by the webcam. You should set the camorama graphical interface to be in foreground to be able to monitor the change produced by the script.
Please tell me what have an effect or no effect on the image.

---

### Post by mattchew on 2008-06-25
Is there a non-kubuntu version that works right now?

I'm still semi new but only saw kconfig but no normal config...am I missing something?

---

### Post by nol_faich on 2008-06-25
Hi Mattchew,

yes you are missing something ! Kconfig stands for "Kernel config" I think, absolutely no relation to KUbuntu.
Just run "./install".
If you have a 0503, for Asus C90S try the "c" version, Asus Z37E try "ms", Medion try "sim" and for a f191 device you don't have to choose.

---

### Post by mattchew on 2008-06-25
> **nol_faich said:**
> Hi Mattchew,

yes you are missing something ! Kconfig stands for "Kernel config" I think, absolutely no relation to KUbuntu.
Just run "./install".
If you have a 0503, for Asus C90S try the "c" version, Asus Z37E try "ms", Medion try "sim" and for a f191 device you don't have to choose.

Yeah I have a C90s same as you.


I also got "cp: cannot stat `gl860.ko': No such file or directory
Creating module dependencies, this may take a while...
FATAL: Module gl860 not found." when I ran install with B...but I didn't see a C option, however B indicated that it was the Asus c90 driver. What download link should I use for NVGL/etc? I've seen a few through these webcam forum links so far (3).

Will test reboot method after work in ~9hrs

---

### Post by nol_faich on 2008-06-25
I think I need to update the install script. "c" is maybe not proposed but you can use it. The tarball is name something 0.2h3. ~9h , it will be midnight for me. I will go sleep about 1h.

---

### Post by blazercist on 2008-06-25
uh nol im confused I went to try the new version and there is changes
```

geoff@geoff-laptop:~/nvgl$ ls
base_gl860.h         gl860-dev-0503.o     gl860.mod.o    Kconfig
gl860-bayer.c        gl860-dev-0503sim.c  gl860.o        Makefile
gl860-bayer.o        gl860-dev.c          gl860-sysfs.c  Makefile.standalone
gl860-buf.c          gl860-dev-f191.c     gl860-sysfs.o  Module.symvers
gl860-buf.o          gl860-dev-f191.o     gl860-usb.c    README
gl860-dev-0503a2.c   gl860-dev.h          gl860-usb.o    relog.c
gl860-dev-0503a.c    gl860-dev.o          gl860-v4l.c    svnvgl
gl860-dev-0503blz.c  gl860.h              gl860-v4l.o
gl860-dev-0503.c     gl860.ko             install
gl860-dev-0503ms.c   gl860.mod.c          Kbuild

```

0503c is gone?

---

### Post by nol_faich on 2008-06-25
"a", "b" and "c" are in the "a" file. Depending on your choice with ./install, it will enable or disable some parts of that file.
If you still have the working driver, please :
* post the result of "dmesg | grep gl860"
* start "camorama -x 640 -y 480 &" and tell me how much time is needed to have an image + use the script in #142 by typing ./shakedown and report to me _for each action_ wether it works or not + test the different sizes listed at the end of ./shakedown.
* "./install blz" and restart your computer after a shutdown to report wether that version works or not.

---

### Post by nol_faich on 2008-06-29
Blazercist? Tricid? Hulkie? Fret_saw?

---

### Post by blazercist on 2008-06-30
Hey I'm sorry for the long delay I have been very busy.  I did try out the new driver, still only "c" works, it is still upside down, but the black bar on the side is now gone.  It still takes about 10 seconds to initialize.  Changing settings in camorama causes a short freeze (about 3-5 seconds).  I have not had a chance to run the script, hopefully I will have time today.

"a" "b" and "blz" did not work at all.

---

### Post by nol_faich on 2008-06-30
OK, if blz did not work, it means that we sometimes need to wait before sending instructions to the webcam.
I uploaded a new release, it should be quickier and i have a new information when a command failed.
I still need the "grep gl860 /var/log/syslog" and the result of the shakedown.

---

### Post by hulkie on 2008-07-01
Hey,

I'm still on that conference, but on friday I'll have plenty of time on the way back to try different things out. I quickly tried with the newest version and the 'ms'-flavor as you suggested but, although the blue light went on, no image was shown (at least after a minute of waiting), with all 3 programs at my disposal (xawtv,cheese and camorama). As I am in the middle of doing calculations for my presentation, I am not able to switch off my computer now. Will let you know more on monday (or possibly already friday).

Can't wait.
Sam.

---

### Post by nol_faich on 2008-07-01
Hi Hulkie! I did not remember you have a Z37sp, I will update the message in the install script. From your logs, I believed you have a C90S. Anyway, you only have to test the "b". This is done from your logs. If it does not work, you will have to try after a restart.
Only test with camorama, if it works, I need "grep gl860 /var/log/syslog" and a report about which tests work or not with the "shakedown" script.

Post-it : Fret_saw and Hulkie : "b".

@ Tricid and Blazercist : you do not need anymore to restart your laptop since the driver "c" works for you.

---

### Post by blazercist on 2008-07-01
nol, the script had some weird effects, all the flip functions did nothing but change the hues to yellow blue red etc, the contrast and lighting functions seemed to work., here is the output of grep gl860 /var/log/syslog, also the black bar seems to appear only in 800x600, 640x480 works fine, 1280x960 seems to have a problem with vertical/horizontal sync and 1600x1200 also seems to have problems with horizontal sync.....  oh it does start much faster :)

---

### Post by nol_faich on 2008-07-01
Ok, please post a PNG picture for all troubles (color, sync, etc). The sync issue appear all the time or after some seconds ?
Your traces seems to be be outdated ? Do you use the last release to make them ?

---

### Post by blazercist on 2008-07-01
i didnt see that you made a new driver, the sync issue doesn't happen all the time only once in a while, i just tried 1280x960 and it worked fine (upsidedown).  The black bar is gone in 800x600 .... 1600x1200 is the only one that always has a sync problem (maybe because my max monitor resolution is only 1680x1050?).  Now for some reason the script has no effect at all.  I am attaching pictures of the sync problem, then i will restart and try the script again.

---

### Post by blazercist on 2008-07-01
Ok, I don't know what I did wrong before, but now almost everything works!!! :)

At least in 640x480...  I ran the script and the flip functions all worked and alot of the other functions worked too, not all but alot.  I took about 20 screenshots and I'm going to try to post them all.  Each screenshot shows the camorama window + the script running term with the last command issued by the script.  The screenshots are all numbered in order so you can see the change from one to the next.

---

### Post by blazercist on 2008-07-01
here are the next 5

---

### Post by blazercist on 2008-07-01
5 more

---

### Post by blazercist on 2008-07-01
last ones, sorry about the million pictures i posted just didnt know any other way.  AND the NEW TRACE from grep gl860 /var/log/syslog (i had to cut out ALOT to make it upload.)

---

### Post by nol_faich on 2008-07-02
I am pleased that it works.
Maybe the driver is not perfect and sometimes the init and capture sequences will be correctly done, and other times badly done and so there will be troubles.
I need the whole traces, to know what can be better in the intialization and start of video stream. Send me a mail with that traces, as you already made once. I also need that traces while you are in 1600x1200 with the sync issue.

About the snapshot, if you have to make further ones, Camorama has a button which allow you to grab the picture it displays (on bottom right of the picture), you to go in the configuration to choose format and directory of the snapshot.

---

### Post by blazercist on 2008-07-02
> **nol_faich said:**
> I am pleased that it works.
Maybe the driver is not perfect and sometimes the init and capture sequences will be correctly done, and other times badly done and so there will be troubles.
I need the whole traces, to know what can be better in the intialization and start of video stream. Send me a mail with that traces, as you already made once. I also need that traces while you are in 1600x1200 with the sync issue.

About the snapshot, if you have to make further ones, Camorama has a button which allow you to grab the picture it displays (on bottom right of the picture), you to go in the configuration to choose format and directory of the snapshot.

i kno camorama has a button, but I get an error when i use it, it says it cant create ~/Webcam_Pictures even tho the folder already exists, anyway I wanted you to be able to see the script alongside the picture so you can tell the changes.  I will try to make a full trace and email it to you this evening. (8 hours from now)

---

### Post by Jan Olieboer on 2008-07-02
Hi,

Great stuff! I think I have the same camera. The c-version of the 0.2h4 driver seems to work best. Does produce a few messages on startup, as attached, but certainly does produce an image, also as attached.

Jan.

---

### Post by nol_faich on 2008-07-02
Hi! Could you make several install/deinstall (for example 5) of the "c" driver (without restart of the laptop and without trying to watch the webcam) and once it is done send a me private message with the result of "dmesg | grep gl860". I would like to see if the errors appear at the same step in the initialisation sequence.

I uploaded a 0.2h4b version but before trying it, make several test as explained above. Taking into account your dmesg snapshot, I add two new delays. I hope it is better.
I made an horizotal and vertical flip of the image. Could you tell me if it is OK horizontaly ? Lift your left hand for example, if that hand is lifted on right of the picture it OK.

---

### Post by blazercist on 2008-07-02
ok so heres the deal i installed the new 2h4b driver and it sortof works.  sometimes it initializes fine and the vflip and hflip are correct BUT, the image is kinda stretched vertically i attach a picture.... other times it does not initialize correctly and i get a screwed up image where the vflip and hflip are wrong.  Im going to pm you the /var/log/syslog seperately.

---

### Post by soro2005 on 2008-07-02
Hey you all. I just got my new Asus S37S and would like to contribute here, but it's all a little confusing. Is there a way anybody can give me a quick heads up, or point me to the post which tells me with which driver to start and how to generate the relevant data/logs? 

I'm almost positive I've tried out all the possibilities in both of the tarballs, but I didn't get any results. The 'ms' flavor seems to be the one that's closest to being read by camorama, but I'm pretty sure that's not the one that's good for me.

I believe I should also have the Windows drivers somewhere, but I don't have a Windows installation, unfortunately.

Also: I've bought my computer from [Zareason](http://www.zareason.com), they might be interested in helping to get this done.

---

### Post by nol_faich on 2008-07-03
Hi soro2005 !
Concerning the Asus S37S, the version is the theoreticaly  the "a". However it does not work. You can help by install that version, restart your computer after a shutdwon and once your are logged sending me the "dmesg | grep gl860".

---

### Post by soro2005 on 2008-07-03
Hey nol_faich: Thanks for all this! Here comes:

```
 dmesg | grep gl860
[   33.802483] gl860: Genesys USB2.0 webcam driver startup
[   33.802518] gl860: Genesys USB2.0 - GL860 based webcam found.
[   33.802519] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
[   33.802522] gl860: Release: 0103
[   33.802523] gl860: Number of interfaces : 1
[   36.016111] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 39
[   36.794308] gl860: ctrl transfer failed -32 [p40 r11 v0000 i0000 lg0] 297
[   36.794359] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
[   36.794406] usbcore: registered new interface driver usb_gl860_driver
[   36.794410] gl860: v0.3.0 : Genesys gl860 USB Video Camera
[   47.245332] gl860: Demande de la taille 640x480
[   47.247214] gl860: réinit à 298
[   48.765775] gl860: Error (-2) re-submitting urb in gl860_isoc_handler:1.
[   48.767758] gl860: Error (-2) re-submitting urb in gl860_isoc_handler:1.
```

---

### Post by nol_faich on 2008-07-03
It seems to me that you tried to watch the webcam, as you have just one real error (-110), I wonder if you have seen something ?

---

### Post by blazercist on 2008-07-03
hey nol did you get my email with the grep gl860 /var/log/syslog ?  was it the correct one?

---

### Post by soro2005 on 2008-07-03
Oh, I hadn't actually tried to watch it, stupid me. Now that I've tried, attached the result. It's from Camorama, and I can actually see some of my hair. It came up after half a minute or so.

*edit: I've changed the screenshot, this one's nicer. I can actually reproduce the behavior it seems (delay etc.), and what you can see in the lower, colored part is the top of my room on its head. So it's upside down down there. The upper part with the diagonal stripes has parts of my face. Plus, I should say that it moves.*

Here is a sample from dmesg. It's three different messages, the first two repeated many more times (snipped). First:

```
[ 1715.162204] gl860: Demande de la taille 800x600
[ 1715.173002] gl860: réinit à 389
[ 1716.915747] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 24
[ 1718.230905] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0034 lg3] 72
[ 1719.458214] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0035 lg3] 85
[ 1720.661425] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0034 lg3] 88
[ 1721.904609] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0035 lg3] 106
[ 1723.106439] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0035 lg3] 108
[ 1724.315148] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0035 lg3] 112
```

Then:
```
[ 1742.636198] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 273
[ 1743.121264] gl860: Frame buffer overflow (480800/480000)!
[ 1743.121273] gl860: Frame buffer overflow (480800/480000)!
[ 1743.123265] gl860: Frame buffer overflow (480758/480000)!
[ 1743.123271] gl860: Frame buffer overflow (480042/480000)!
[ 1743.123275] gl860: Frame buffer overflow (480554/480000)!
[ 1743.123277] gl860: Frame buffer overflow (480246/480000)!
[ 1743.123280] gl860: Frame buffer overflow (480454/480000)!
[ 1743.123283] gl860: Frame buffer overflow (480346/480000)!
[ 1743.123286] gl860: Frame buffer overflow (480350/480000)!
[ 1743.123288] gl860: Frame buffer overflow (480450/480000)!
[ 1743.123291] gl860: Frame buffer overflow (480250/480000)!
[ 1743.329153] gl860: Frame buffer overflow (480267/480000)!
[ 1743.329161] gl860: Frame buffer overflow (480283/480000)!
[ 1743.329164] gl860: Frame buffer overflow (480413/480000)!
[ 1743.329167] gl860: Frame buffer overflow (480387/480000)!
[ 1743.329170] gl860: Frame buffer overflow (480209/480000)!
[ 1743.329173] gl860: Frame buffer overflow (480591/480000)!
[ 1743.329176] gl860: Frame buffer overflow (480109/480000)!
```

Finally:
```
[ 1749.111976] gl860: Frame buffer overflow (481098/480000)!
[ 1749.111978] gl860: Frame buffer overflow (482102/480000)!
[ 1749.111981] gl860: Frame buffer overflow (480842/480000)!
[ 1750.147416] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 385
[ 1751.634593] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 400
[ 1752.845778] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 407
[ 1754.053119] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 412
[ 1755.256330] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 415
[ 1756.480027] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 426
[ 1757.702850] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 438
[ 1758.914176] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 445
[ 1760.117392] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 449
[ 1761.320598] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 453
[ 1762.535928] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 462
[ 1763.787112] gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3] 485
[ 1822.483445] gl860: Error (-2) re-submitting urb in gl860_isoc_handler:1.
[ 1822.485442] gl860: Error (-2) re-submitting urb in gl860_isoc_handler:1.
```

The last snippet, I guess, is from where I have closed Camorama.

---

### Post by nol_faich on 2008-07-03
Yes I got it Blazercist. I will try to post a modified version this friday.

---

### Post by soro2005 on 2008-07-04
The one above was with the 'a' driver from the gl860_0.2h4b.tgz package. Attached the same with the 'a' driver from the gl860_0.2h4.tgz package. I got the impression that it took a little longer until camorama came up (perhaps two min), and the lower half of the screen tends to flicker. Not sure this is useful.

---

### Post by nol_faich on 2008-07-04
The slowness issue is due to the timeout for usb transfert : when we send something, the webcam must acknowledge for that and we wait for that acknowledgement until the timeout is expired. Expired timeouts are the shown with the -110 error. Each time there is a -110, you have been waiting. I think we have timeout because after a sending to the webcam, it does something and if we send directly a new instruction without waiting a little bit, the webcam does not understand any more what happens and become temporary inert.
The "0.2h4b" version has shorter timeout, this is why it is quicker.
What i learned from you and Blazercist is that the timeouts happen with different transfert, not the sames, so I must delay each transfert.
The problem is that I test on my own 05e3:f191 device and it becomes ssslllllooooowwwwwww although there is far less sendings to do. I am afread for you so, however the original userspace driver for your device uses 50 ms delays. I will reuse them.

You can test that by adding "msleep(50);" (without ")in gl640-usb.c at the end of the function fct_RTx and just before the "return" instruction of that function.
Use dmesg | grep gl860 to see which time it needs to initialize (time between the detection of the 0503 webcam and the announce of the control of /dev/video0 or 1). You can also see how long is the LED of the webcam switched on. If it is too long try 15, then 5 thus 1 instead of "50" in "msleep".
If it is quick, you can try to watch the webcam.

---

### Post by soro2005 on 2008-07-04
Wow! Attached a colorful and dirty mousepad, taken in camorama, with msleep(25);
It's upside down if that's not appartent. I now only seem to be getting thes in dmesg:
```
[  203.752721] gl860: Frame buffer overflow (480800/480000)!
```

I will experiment a little more with this, and also with other settings if you tell me which, but now have to run. Many thanks already, this looks like you're very close to at least cracking my model.

---

### Post by nol_faich on 2008-07-04
Yes !
Is it ALWAYS "480800/480000" ? It could mean that the image is 800x601 instead of 800x600 (800x6001=480800).
Important, could post the "dmesg | grep gl860" in order to know what time is needed for initialization ?
Could you run the script "shakedown" and me what work and have no effect ?
Thanks
I add the "msleep(25);" for the "a", "b" and "c" and I'll update the SF repository.

---

### Post by soro2005 on 2008-07-04
I've just used it for Skype :D Works like a charm, upside down of course, and takes a little time to start up.

I have a friend over and am under the influence atm, will run some more tests to try and figure out the best delay as soon as I have my head clear again. Thanks so much for the moment!

---

### Post by nol_faich on 2008-07-04
I didn't know what I did, but now the version is online at SF.

New release at SF with a 15ms delay to try to be almost twice quicker.
To be tested for "a"/"b"/"c" flavors according to your working configuration.

---

### Post by soro2005 on 2008-07-05
Okay, so this is with the new driver in "a". It still takes like half a minute or so to boot up, and in Cheese, I get something a little out of shape. Either like the one in the first photo below, or alternatively a full frame, but with the image falling through, left to right. There seems to be a problem syncing the dimensions or whatever.

In Camorama, I now seem to reliably get a good and stable image (again after having to wait for like half a minute), and once (chime) I saw myself facing a shockingly clear and bright picture. That's the second shot below with some colors everybody here knows well. Normally, it's rather on the dark side, sort of like in the first screenshot.

Keep it up, and I still owe you more details on the dmesg output. Still have a friend over, just had to sneak out for a few minutes to see how the webcam was doing. :guitar:

---

### Post by nol_faich on 2008-07-06
There may be instabilities due to the shorter delay of 15ms compared to your 25ms.
It is not normal it needs 30s to be working. We have to make about 600 sendings to the webcam and with 15ms delays, it should take at least 9s. 20s are still unexplained.
I don't know the response time of the webcam, but in most cases it does not exceed 15ms. I will study the usb debug mode in linux to log the sendings ans their time code. Jointly with the dmesg, it should be possible to have a better idea of what happens while running linux.
I forced the inversion of your images because of your first former snapshot but obviously it was not useful.

---

### Post by blazercist on 2008-07-06
the new driver works very well, the startup time is 15 seconds.  the image is the correct orientation now and brightness contrast white balance all work.  thank you nol :)

---

### Post by nol_faich on 2008-07-06
New release on SF : new relog, it shows the delay between each sending. If someone can compile it and make several logs with Windows containing a webcam viewer start ans some second of image, it could useful to have shorter launch time.


I also add an experimental version with shortened waiting time, please test it (0.2m_expc).


About the logs, I need :
- changes of light source ;
- Fret_saw/Hulkie : change in size to 800x600, 1280x960 and 1600x1200 ;
- for C90 I also need a log while a viewer is already started : you have to rotate the webcam so that it goes from a front screen view to a back view. We can ask to the webcam for which its sight state is in order to automatically correct the image.

---

### Post by soro2005 on 2008-07-06
Works great here. The expc is not quite as stable. It sometimes starts upside down, even in Camorama. The other one (0.2m) starts right side up in Camorama (ca. 15 sec.), and in Cheese upside down (takes a little longer), or sometimes severly screwed up as in the screenshot I have posted some posts above.

In Camorama, the camera reacts to change in lights. It seems to adapt the white balance on the fly, but it's night here and I don't have too many different light tones around.

I would like to generate the logs you request, but I have to admit I don't quite understand how to get to them. The dmesg yields the sam frame buffer overflows as always. Could you give a little more detailed instructions? Also the shakedown script. Where do I run it?

Thanks again! This is truly brilliant work!

---

### Post by hulkie on 2008-07-07
Hello Nol,

the driver is working perfectly (the one that was online last thursday, so not the latest)! But the 'c' version, not the 'b'. I installed the 'b' version first and it did work, once I restarted the computer, but it took a long time to start up (like 1-2 minutes) and often the image was all distorted (green zones, bad sync,...), but at times it was perfect. Then I tried the 'c' version and this works flawlessly. Starting up Camorama takes only 10 seconds and all settings appear to work. There was only 1 glitch and that was that the image is upside down, and in mirror view. However, simply setting hflip and vflip = 1 fixes this. Although I was surprised that hflip means flipping around a horizontal line and thus fixing the 'vertical' issue, everything is fine. I also have performed the shakedown script (just run this in a separate terminal when camorama is online..) and most settings appear to work although some do not have a big effect (sharpness from low to middle for instance, but high sharpness had the expected result). I have a zip file with the resulting pictures (12Mb), do I mail them to you? 

Resolutions 640x480 and 800x600 both work, but the larger resolutions do not. This typically results in an image as in the attachment. Therefore, I redid the logs on these configurations. I hope they are ok, because I did not see the images in the webcam in windows on vmware. Perhaps because I was working on battery, but hopefully the control sequence was still send to the webcam. In each of the logs, I switched back and forth between 640x480 and the larger resolution a couple of times. I saw that you created a new relog, so I will relog shortly.. :)

And then some bad news, today, the (same) driver was more erratic than last friday. Then I started and restarted it several times without any problem whatsoever, but now 3 out of the five times tried, there was a black bar at the right side. 
$ tail -f /var/log/syslog | grep gl860 > overflowing.txt
revealed the following: 
gl860: Frame buffer overflow (482141/480000)!
gl860: Frame buffer overflow (481669/480000)!
gl860: Frame buffer overflow (482106/480000)!
gl860: Frame buffer overflow (480623/480000)!
gl860: Frame buffer overflow (481777/480000)!
gl860: Frame buffer overflow (482016/480000)!
gl860: Frame buffer overflow (481984/480000)!

in the full overflowing.txt, I restarted camorama several times.. I also added the dmesg (in the session I unloaded and reloaded the module once, to try and get rid of the black bar)

So, that's it for now. I will reinstall the new driver today and tell you what happened tomorrow. Are there any other things I need to do?

Thanks again for an already brilliant driver.
Hulkie.

---

### Post by nol_faich on 2008-07-07
Wouawwwwww! Maybe one less driver, only four flavors.
Could you tell me if the -2 error in dmesg is related to a change in size OR if the image gets scrambled and you change the size to cancel the scrambling. In the first case, it is not a very error.

---

### Post by soro2005 on 2008-07-07
I'm asking about the shakedown b/c evey single test just yield "No such file or directory" if I run it from the extracted tarball. :( Also, the Adjustments in Camorama work at best sporadically. Perhaps that's the same issue?

---

### Post by nol_faich on 2008-07-07
If there is that error, it the directory used in the script is not good for you.
The driver creates a directory in /sys/.../video0 (or one I you still have a video device) and in the directory there is file you can read (get value from the driver) or write (set value in the driver).
Theoretically, the script search for the good video but maybe it does  not work properly with you.
In the dmseg, the driver says which video it is.
If it does not work, try something like "find /sys -name 'video.*'" and use the replace the path in the script by the good one.

---

### Post by soro2005 on 2008-07-07
Ah, okay. Are you interested at this point in a full log of working features? Here a quick breakdown: Saturation, colour and lightsource do not seem to have any effect on my setup. Whiteness does something, but it's not changing colour tones if that's what should happen. The image gets a little darker or lighter. Something seems to happen with freq50, but I'm not sure what should happen. All the others have a noticeable effect that seems to be in tune with the name of the key in question.

---

### Post by nol_faich on 2008-07-07
Ok, so no log.
Have you tried the "0.2m_expc"? in that case, could you tell how much time it needs to initialize? Also when you install it, the blue LED is witched on how much time? Could you post a "dmesg | grep gl860" to see if there is error.
Could you also answer for the -2 error.

@ Whose who still have Windows : i just need a log with light source changes.

---

### Post by nol_faich on 2008-07-07
I add on SF a new experimental version (0.2m_expd). I need that you try it by making some size changes and several times start and stop camorama. I suppress half sent data as they are already in the initialization sequence when the webcam is first probed. I think these data are mandatory but maybe this may work.

---

### Post by soro2005 on 2008-07-07
> **nol_faich said:**
> I add on SF a new experimental version (0.2m_expd). I need that you try it by making some size changes and several times start and stop camorama. I suppress half sent data as they are already in the initialization sequence when the webcam is first probed. I think these data are mandatory but maybe this may work.

This starts like a rocket (~5 sec in Camorama, on the second time the indicator lights up), and it seems to start reliably here (version "a", as always). It also comes up quick and nice in Skype. In gstreamer-properties and Cheese, I only get noise. May that be b/c gstreamer tries to open it too big?

This seems to be better/more reliable in Camorama than the last experimental version.

Attached the dmesg trace, the "Frame buffer overflow (1921438/1920000)!"s correspond to Cheese and gstreamer if I'm not mistaken.

---

### Post by soro2005 on 2008-07-07
Here a more concise dmesg log. It is first Skype at 320X240, then I have started Camorama several times at different resolutions. The 80x60 is from the menu, I belive, by changing to "small", then I have changed to "large" which results in an entirely messed up image and the last frame buffer overflows. That resolution may simply be too much for my cam, although it says 2.0 Megapixel. This is, again, with flavor "a" of 0.2m_expd

```
[ 2615.572017] gl860: Demande de la taille 320x240
[ 2615.582038] gl860: réinit à 105
[ 2618.130841] gl860: réinit à 103
[ 2964.072542] gl860: Demande de la taille 640x480
[ 2964.074359] gl860: réinit à 365
[ 2966.610165] gl860: Demande de la taille 800x600
[ 2966.619927] gl860: réinit à 105
[ 2988.231412] gl860: Demande de la taille 640x480
[ 2988.233560] gl860: réinit à 176
[ 2988.331151] gl860: Frame buffer overflow (307897/307200)!
[ 2988.435097] gl860: Frame buffer overflow (307929/307200)!
[ 2988.541031] gl860: Frame buffer overflow (307961/307200)!
[ 2988.644983] gl860: Frame buffer overflow (307993/307200)!
[ 2988.888840] gl860: Frame buffer overflow (307360/307200)!
[ 2990.915358] gl860: Demande de la taille 640x480
[ 2990.924707] gl860: réinit à 105
[ 3029.801722] gl860: Demande de la taille 640x480
[ 3029.805056] gl860: réinit à 147
[ 3032.330188] gl860: Demande de la taille 320x240
[ 3032.339970] gl860: réinit à 105
[ 3040.868925] gl860: Demande de la taille 800x600
[ 3040.878976] gl860: réinit à 162
[ 3043.567291] gl860: Demande de la taille 80x60
[ 3043.576382] gl860: réinit à 113
[ 3043.621632] gl860: Frame buffer overflow (308000/307200)!
[ 3043.653618] gl860: Frame buffer overflow (308362/307200)!
[ 3043.745558] gl860: Frame buffer overflow (307589/307200)!
[ 3043.849506] gl860: Frame buffer overflow (307621/307200)!
[ 3043.953453] gl860: Frame buffer overflow (307654/307200)!
[ 3044.083374] gl860: Frame buffer overflow (307405/307200)!
[ 3050.618985] gl860: Demande de la taille 80x60
[ 3050.629357] gl860: réinit à 149
[ 3053.127257] gl860:  ** 0204 (0) **
[ 3053.170424] gl860: Demande de la taille 1600x1200
[ 3053.180202] gl860: réinit à 105
[ 3054.968380] gl860: Frame buffer overflow (1921014/1920000)!
[ 3055.262212] gl860: Frame buffer overflow (1921140/1920000)!
[ 3055.658002] gl860: Frame buffer overflow (1920033/1920000)!
```

---

### Post by nol_faich on 2008-07-08
The webcam is really 1600x1200 capable.
I don't think sent data are false, maybe I have to change something in the allocated bandwidth. Can you watch Camorama in 800x600 or 640x480 for 30s and says if in the dmesg you are also in overflow for that 30s or just at the beginning ?
Cheese and Gstreamer asked for 1600x1200?

---

### Post by soro2005 on 2008-07-08
640x480 Has a bunch of these while starting, and then nothing (number of the frame varies):
```
[  566.595821] gl860: Iso frame 1 of USB has error -71
```
800x600 seems to be throwing the same error when started after the camera has been started before with the same resolution, and there seems to be sometimes the Frame buffer overflow error during start. While it's running, I don't currently get any error messages.

If I start camorama in 1024x768, I get the same errors as with 800x600 and the image starts fine, but with what looks like a resolution of 800x600. There is a black frame around the image. The same with 1200x900 (with a wider black frame) and up to 1260x945. At 1280x960, the image fills out the frame again, and it is sometimes stable and big, but sometimes garbled. With or without a stable image, I get a Frame buffer overflow about evey second. At 1600x1200, the image fills out the frame, but it is not stable. I get the Frame buffer overflow about every second.

Cheese requests 1600x1200. Gstreamer-properties currently segfaults when I try to test video in. But yesterday it worked and also requested 1600x1200. Not surprisingly. I think cheese just takes gstreamers default.

---

### Post by nol_faich on 2008-07-08
The driver does not resize then image. It propose 640x480, 800x600, 1280x960 and 1600x1200. When the driver composes the RVB image, it is able to take one line out of two, one out of three, and so on so you have small resolutions. out of that resolution, the driver takes the biggest which is less than request and add a black frame around to fill the requested size.
That is part of what can be better on the driver but i don't know if the resizement is to be done by the driver (cpu-consumming and so not the best solution) or if this must be done by the soft who ask for the image. if that is the case, i just have to refuse the requested size. Ekiga should be able to resize itself if we don't provide it the requested size. I will try with amsn, camorama and xawtv.
Tonight, I will upload a new release because due to proxy issue, I wasn't able to do that. I use a bigger bandwidth and there is also so additions. You can enlarge the bandwidth by changing in gl860.h the ISO_FRAME_DESC_BY_SEC or something like that from 16 to 32.

---

### Post by Jan Olieboer on 2008-07-08
Hi Nol,

Tried the latest drivers and the 0.2m_expc c-version seems to do quite a good job. Works well, with a few messages still .. but with a reasonably stable image! Fantastic .. well done! The expd version however doesn't produce an image with camorama at all. I have re-installed Vista, and can make logs with USBsnoop. If you need any, please let me know. I have an Asus C90S-AK006C. Maybe it should be checked which C90S extensions we all have here .. there might be other ones then the AK006C .. not sure if there are any. This number can be found on the bottom of the machine.

Cheers,
Jan Olieboer.

---

### Post by nol_faich on 2008-07-08
@ all : New release. In that release I use a bigger bandwidth and I log in dmesg a new information which allows maybe to identify which sensor you have and so the driver to use.
I need :
* the 'dmesg | grep "gl860.*probe"' along with the driver you use.
* to know if the 1280x960 and 1600x1200 work and are stable, watch one minute for example.

@ Jan : If there is not any image, I need the "dmesg | grep gl860" to see if there is errors during the initialization. If you can make a log in windows with changes of light source, it well help to close the parameters logs.

---

### Post by soro2005 on 2008-07-08
Compilation fails with:

```
/home/xxxxxx/source/tarballs/m-expe/nvgl/gl860-usb.c: In function &#8216;fct_RTx&#8217;:
/home/xxxxxx/source/tarballs/m-expe/nvgl/gl860-usb.c:626: error: &#8216;cpt&#8217; undeclared (first use in this function)
/home/xxxxxx/source/tarballs/m-expe/nvgl/gl860-usb.c:626: error: (Each undeclared identifier is reported only once
/home/xxxxxx/source/tarballs/m-expe/nvgl/gl860-usb.c:626: error: for each function it appears in.)
make[2]: *** [/home/xxxxxx/source/tarballs/m-expe/nvgl/gl860-usb.o] Error 1
make[1]: *** [_module_/home/xxxxxx/source/tarballs/m-expe/nvgl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
```

---

### Post by nol_faich on 2008-07-08
You're right. I made a mistake. The release online is now OK.
Really sorry.

---

### Post by soro2005 on 2008-07-08
No reason for you to say sorry for a little bug. :)

1280x960 works sometimes more or less, but worse, rather than better, than the last version. Mostly its garbled. 1600x1200 is still always garbled. The errors are the same as before. 800x600 runs for minutes without any error messages. I have the very subjective impression that the image quality is higher than before. 640x480 throws a few Frame buffer overflow before it starts, and then runs for minutes without error messages.

That's with m_expe_OK, version a.

---

### Post by nol_faich on 2008-07-08
What a shame, the big size issue is not resolved. Could you post a dmesg with the big sizes and the value of "probe" in dmesg ?

Quite strangely it is OK and stable in big size for another S37S on a French forum. For the "ms", out of the two testers, one needs to be slowed, not the other.

---

### Post by soro2005 on 2008-07-08
Attached. That's first 1280x960 and then 1600x1200.

Yeah, it's a shame it didn't solve it. But it seems to me that you're going to crack that one as well. I'm using my webcam very happily on Skype already, and everybody is impressed by the high quality.

May this have to do with the gpu? Compiz? I will try to switch off the computer for a minute or two, to see whether that's doing the trick (as opposed to just restarting it).

---

### Post by nol_faich on 2008-07-08
@Soro2005 : the ligne with "probe" in the dmesg is missing, could you give "dmesg | grep probe". Thx

@ all : Images have to be resized by the driver. Neither aMsn nor camorama are able to do that.

---

### Post by soro2005 on 2008-07-08
Ah, sorry, forgot to mention. I don't get any line with "probe." I've tried several times, by tailing syslog and with dmesg, and I haven't been able to find anything with "probe." :confused:

---

### Post by nol_faich on 2008-07-09
@ Soro2005 : I download the tarball and the "probe" line shall appear. Are you sure you use the 0.2_expe_OK ?

@ All : shutdown of the laptop is no more useful as the driver works, there is no more case where the driver can block the webcam because it does not understand what is received.

---

### Post by soro2005 on 2008-07-09
Oh, sorry, it's probably lost some time after the module is loaded. Here it is, hope that's the correct one:
```
[   43.352712] gl860: probe= 0
[  247.909180] gl860: probe= 0
```

---

### Post by nol_faich on 2008-07-09
It will be hard to identify which driver to use according to the probed value because there is four drivers and only to answers : 0 and 255.

For the 1280 and 1600, I would like a snapshot of the scrambled image and the associated dmesg. If it is as seen before (BW small images with sync issue contained in a 1600x1200 image), that means some data are not well sent.
I know that the "a" works for someone with all sizes but maybe there is something bad in the driver as both size are treated together.

---

### Post by soro2005 on 2008-07-09
Here comes. There are at least four different patterns. The one in 1600X1200-1 I think I have only evern seen in that resolution. It is quite typical for that resolution. The one with the small images also occurs in 1600x1200. The dmesg.txt file contains the messages while taking the first pictures of each size. The ones for the second ones look very similar. Does certainly not look like it's going to be easy to recognize a pattern, but if you think that it might be helpful, I can certainly take the time to try to separate the logs more clearly from each other.

I have actually also seen clear images in 1600X1200. But that's once every while, and dmesg for those times also doesn't look much different.

---

### Post by nol_faich on 2008-07-10
I've never seen that sort of pics ! I'll study again what I did and the big size logs of Hulkie.

---

### Post by hulkie on 2008-07-10
Hey,

I have not tried the newest driver yet as I am just reading the updates since last time, but before you look at my old logs, I redid them with a newer relog and they are in attachment.

I also noted, typing dmesg repeatedly at different instants that he spits out that error message number two each time I switch off camorama (in e.g. a working 800x600 mode). That happens with each switch off, so perhaps there is still something missing in that sequence? But this does not have any bad side effects.

I also attached the typical image I obtained with the older driver at 1600x1200 (before the bandwith modificiations). I will post back when I have tried the new driver this evening.

Hulkie.

---

### Post by nol_faich on 2008-07-10
The -2 is corrected in the newer driver. I took a look at your dmesg and those of others and I noticed that it only occurs before size change and at the end of the dmesg and I saw from the source code that if that was a real error, there must be another error message. It is something else surprising about the webcam. The error most of you gets when the camera switch off is not the same as mine. Thanks for your research. I omit to tell that the -2 was solved.

I will look at your logs.

---

### Post by soro2005 on 2008-07-11
Count on me if you need me to test something more/else. Of course, I'm quite happy that I can use the cam for Skype, for which it works, according to my friends on the other end of the line, beautifully. :)

---

### Post by nol_faich on 2008-07-12
0.2n released. I made no changes in the driver code but I add a script intended to give me info on the webcam response time and real sleeping time of the msleep.
For that the script uses usbmon to tape USB communications.

Please open two terminals in the "nvgl" directory. In the first type "monusb your_name". Once done, in the second terminal type "./install". Launch camorama and once you have an image stop it. Kill the monusb job in the other directory and follow the notice displayed.
Send me the file "your_name". I will use it to infer the know which time is needed for the webcam to answer when we have sent it some data.

Also, whose with the "c" driver, could you try the "b" version in 1280 and 1600 sizes ?


@ Hulkie : in your logs I have some data about sleeping time for the driver and also some unexpected things in the normal job. As Fret_saw you have data sent to the webcam which are not sent by the "a" driver, nor the "c" theoretically. I will maybe add them.

---

### Post by soro2005 on 2008-07-12
Here comes mine. This one actually comes up most of the time with a good image, albeit mostly upside down and very blue. After unloading usbmon, I've even seen it once or twice with the correct orientation in the big resolution. I've also had it a couple of times coming up with the small b/w images inside the big frame, to then switch over to the full resolution upside down after a second or so.

This is with camorama launched in its default resolution (800x600 I believe).

---

### Post by blazercist on 2008-07-13
hey nol, version "n" doesnt work at all for me i tried "c" and "b" neither work, camorama freezes before I get an image but, camorama does seem to open slightly faster.  Would you like for me to send you the usbmon results anyway?  Version "m" of the driver worked fine.

---

### Post by Jan Olieboer on 2008-07-13
Hi Nol,

Same thing here. No error message from the driver in messages upon startup, but a few when camorama starts, and no image in camorama. I do have the usbmon export, but not sure if this would help you. I can attach my dmesg output. You can observe a few re-installs, starting with the c-version, then the b and then back to c.

Jan.

---

### Post by Jan Olieboer on 2008-07-13
Hi blazercist,

I was looking at the specs you supply for your C90S. Is your processor running at 2.13Ghz? Do you have a T8100 processor instead of an E6600? There are several versions of this C90S. I have the AK006C, but I know there's a AK037C as well (see bottom of laptop), which has a T8100 preocessor I believe.. might also have a slightly different camera .. ?

Jan

---

### Post by blazercist on 2008-07-13
hey Jan, there is no AK006C or AK037C on the bottom of the laptop here is cpu info

geoff@geoff-laptop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz
stepping	: 6
cpu MHz		: 1596.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4270.48
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz
stepping	: 6
cpu MHz		: 1596.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4266.68
clflush size	: 64

---

### Post by nol_faich on 2008-07-14
I looked at the files of the two former releases and I saw a difference in the 503a driver. I released a 0.2n2 with the previous 0503a. Could you test it and make the usb log. I have actually only the soro2005 and I would like to have other logs to see if it is the same charracteristics for everybody.

---

### Post by hulkie on 2008-07-15
Hey Nol,

I just tried the newest driver n2, and I am also not seeing anything in camorama. The driver I am using currently and which works fine is the 0.2m edition. With this driver I also tried the usbmon utility and the result is in attachment. I also tried the 'b' flavor of the 0.2m driver with the higher resolutions and it gave me the same result as the 'c' version.

Hope this helps.
Hulkie

---

### Post by nol_faich on 2008-07-15
OK Hulkie
Just to be sure : "0.2m" mean "version 0.2m"? Not "release 0.2m" (in that you may run without problem "0.2m_expe_OK").
If it is "version 0.2m", does the "0.2m_expe_OK" work for you?

---

### Post by nol_faich on 2008-07-16
Still no change in the communication part, but now the drivers handles image resizing (infos in the release notes).

---

### Post by soro2005 on 2008-07-16
0.2n3 (a) doesn't work at all for me. Error message from camorama: "Unable to capture image". The dmesg (probably not very enlightening):
```
[   44.192426] gl860: Genesys USB2.0 webcam driver startup
[   44.192464] gl860: Genesys USB2.0 - GL860 based webcam found.
[   44.192466] gl860: Genesys USB2.0 2.0M WebCam - Product ID 0x0503.
[   44.192468] gl860: Release: 0103
[   44.192469] gl860: Number of interfaces : 1
[   44.994103] gl860: probe= 0
[   51.229342] gl860: Genesys USB2.0 Camera is now controlling video device /dev/video0
[   51.229379] usbcore: registered new interface driver usb_gl860_driver
[   51.229383] gl860: v0.3.0 : Genesys gl860 USB Video Camera
[   66.321820] gl860: Demande de la taille 640x480
[   68.805162] gl860:  ** 8223 (0) **
[  147.221901] gl860: Demande de la taille 640x480
[  149.757070] gl860: Demande de la taille 800x600
```

---

### Post by blazercist on 2008-07-16
hey nol, with drivers 0.2m, 0.2n2 and 0.2n3 using all versions "a,b,c,sim,ms" camorama gives error unable to capture image

---

### Post by blazercist on 2008-07-16
oh and nol you took the older releases off sourceforge so i cant even go back to a working one...  :(

---

### Post by soro2005 on 2008-07-16
> **blazercist said:**
> oh and nol you took the older releases off sourceforge so i cant even go back to a working one...  :(

Was 0.2l any good for you? (attached)

---

### Post by nol_faich on 2008-07-17
With camorama is there any other informations ? Launch it in command line, maybe there will be some more things.
Tell me if the "l" works or not.

Soro2005 : the dmesg looks normal, no error, that is really crazy.

---

### Post by hulkie on 2008-07-17
Hey Nol,

yes, the expe_OK driver was also working if I remember correctly, but I did not keep a copy of it, so I reverted to the 0.2m version. Also, to give some better news, with this driver, the 1280x960 was working correctly at one point (see attachment). But, not every time though. 

Hulkie.

---

### Post by nol_faich on 2008-07-17
Can you make several try to watch in 1280 and 1600 and post a copy of the "dmesg | grep gl860" along with the result of each try (size 1280/1600 : working, not working).

---

### Post by hulkie on 2008-07-17
Sure,

here they are. These are for 3 consecutive times (the times after this it was always the third type of image) and the first image was correct color and upright. 

I also retried the expe_ok and it did not work correctly. so I am using the basic m version again. One thing I noticed but did not mention yet, is that the camera light always comes on 2 times. Open opening camorama, it lights up after 5 seconds and stays on for a couple of seconds, then it switches off again. and 4 seconds later it comes on again, after which the camorama ui gets loaded. in the dmesg I also noticed that first a 640x480 image is asked first, and only then, the correct resolution I asked for. I have no idea if this is normal, but maybe you ask for the 640x480 size in the init sequence, where you could ask for the really wanted size directly? Or perhaps this is just how camorama works.. 

Hulkie.

---

### Post by nol_faich on 2008-07-17
All dmesg are unusable because there is not the data when the size change is requested. That is because of overflows, maybe you could find the right data in /var/log/message or previous ones (message.0), etc. Also maybe in syslog. (Is the color OK for the third type of image or is there always a light source (i still need these logs, with 5s between each change!) type issue?)
If I remember, the difference between the "m" and "exp"/"n" is that it has longer waiting delay after sending something, longer timeout and no retry in case of timeout. I will try in one hour to make a "n3" with longer delays, timeout and no retry. From you it seems not useful to wait for a long time before sending something new. I will try to finish the search for right delays in 7 hours.
The driver is defaulted to 640x480, I will look at what happens at the beginning and if it is possible nothing to do before a size is asked.

---

### Post by nol_faich on 2008-07-17
I can't access SF because of proxy concern.
In gl860-usb.c, line 611, change the "nbessai<6" to "<1" (the line must be "while (r<0 && nbessai<1);")
and replace the three "500/2" or "600/2" in lines 604/606/608 and 618/620/622 by "500" or "600". To avoid issue, restart your computer after installation.

---

### Post by nol_faich on 2008-07-17
New release on SF, still not make the delay modifications, but there is no more video stream started in 640x480 before being stopped by the webcam viewer which also ask for the video stream.
I have with that version my first "unable to capture" from camorama. From the log it appears that the webcam stopped, no more data received and it was unplugged before being replugged (this is an embedded webcam, as yours). When it happened, I was doing nothing but rotating the webcam. I have no explanation.

---

### Post by blazercist on 2008-07-17
yea the new version still doesnt work, the last working version for me is 0.2l

---

### Post by nol_faich on 2008-07-18
When you had "unable to capture etc", was it at the camorama startup or had you an image and later the problem ?
I will study the difference between both 0.2l and 0.2n.

---

### Post by blazercist on 2008-07-18
nol, it happens on camorama startup I never get an image.

---

### Post by theZoid on 2008-07-18
I'm just getting in on this....I have a Genesys Logic webcam in my Asus C90s....where can I get the drivers to test?  (this is a Mandriva machine)  Thanks !

---

### Post by blazercist on 2008-07-18
> **theZoid said:**
> I'm just getting in on this....I have a Genesys Logic webcam in my Asus C90s....where can I get the drivers to test?  (this is a Mandriva machine)  Thanks !

I suggest following the link in nol's signature to sourceforge and using the 0.2l driver as thats the last working version for me and I have the Asus C90 as well.  You may also want to try the newest version to see if you get a different result than the rest of us.

---

### Post by nol_faich on 2008-07-18
New release which goes back in some points.

---

### Post by soro2005 on 2008-07-18
The same. I never get an image, just "unable to capture." That's with 0.2n4, the "a" flavor.

---

### Post by nol_faich on 2008-07-18
Is it possible access your laptop with ssh in order to make tests ?

---

### Post by soro2005 on 2008-07-18
> **nol_faich said:**
> Is it possible access your laptop with ssh in order to make tests ?

Is that for me? I can't forward ports, sorry. Also, please don't take offense, but you'd need root access I assume. :-k

---

### Post by nol_faich on 2008-07-18
Ok ! It is not useful to be root ! In fact we have to log into a simple account. From that with "screen", we can make as in VNC but in text mode. I type "su smth", you type the password and you can see everytime what I do.

Release 0.2n5 with still an old thing added again.

EDIT : Release 0.2n5b, the 0.2n5 was not suitable for 0503.

---

### Post by hulkie on 2008-07-19
Hey,

I did some tests, comparing the newest version I had (0.2n3) versus the working 0.2m version. I tried which files I could replace in the old driver with the newer versions without breaking the driver. I found that bayer, usb, gl860_dev.c could be updated without problem. Replacing the v4l file resulted in the acces denied error. And replacing the gl860_dev_0503a file resulted in a different error; camorama did not complain about acces denied, but no images were shown; a blank camorama gui was shown. 

When I changed the usb file, the first time I also obtained an acces denied error, but afterwards this did not return again.. So perhaps, something is too different there as well.

Anyway, I will have more time in the next 3 weeks, so I will dig into the differences a bit more, and try to work out where the regression lies, trying out the different releases. I can understand that this is almost impossible to work out for you, as you don't have the webcam yourself. If I can't find the problem as well, I will look into an ssh access, but I'm not sure if this will work with my internet connection.

I hope we can fix this in the couple of days to come.
Hulkie.

---

### Post by nol_faich on 2008-07-19
Thanks for your tries Hulkie. Could you try with the 0.2n5c and if it does not work replace files in the "m" version ?
The tests MUST be done with camorama. The use of aMsn, Ekiga or Xawtv may lock the system with the file changes.

EDIT : I looked at the v4l and I made a minor change, 0.2n5c

EDIT2 : I made a 0.2n5d with a slightly modified v4l from the 0.2m version (to take into account the image resizing). By default it uses almost the current version of v4l but if it does not work, you replace it with "cp mgl860-v4l.c gl860-v4l.c". before compiling.

---

### Post by soro2005 on 2008-07-19
As is, 0.2n5d here gives "unable to capture". By dropping in mgl860-v4l.c as you indicate, I get a good image, albeit mostly upside down or with the small b/w images inside the big one on resolutions higher than 800x600. It takes a little longer to come up, but that's probably part of the roll-back you've done. How should we test this? What logs/info do you need now?

Let me know if you think that some of the stuff you would like to do through ssh can also be done in an IRC or IM session. I'm heavily firewalled most of the time, and on the move.

---

### Post by nol_faich on 2008-07-19
Brillant Hulkie/Soro2005 and stupid me! I inverted things for VGA limited-webcam and 1600x1200 ones. As I have a 1280x960 limited, all works for me.
Release 0.2n5e online. In the roll-back I added again the initialization sequence which is sent before size-specific instructions because without them Hulkie had troubles. Maybe it is only the case for "c" version of the driver.
I began to include delays issue from the Hulkie logs. If the driver works, the next step will be to reduce their duration by changing the value in the "msleep(16);" in the "fct_RTx" function of gl860-usb.c. 5ms instead of 16 should sufficient.


Can you tell me Soro2005 if in the "/var/log/syslog" there is a bunch of -71 errors and something like :

Jul 20 00:13:23 portabol kernel: [41899.572000] gl860: Iso frame 25 of USB has error -71
Jul 20 00:13:23 portabol kernel: [41899.572000] gl860: Iso frame 26 of USB has error -71
Jul 20 00:13:23 portabol kernel: [41899.572000] gl860: Iso frame 27 of USB has error -71
Jul 20 00:13:23 portabol kernel: [41899.572000] gl860: Iso frame 28 of USB has error -71
Jul 20 00:13:23 portabol kernel: [41899.572000] gl860: Iso frame 29 of USB has error -71
Jul 20 00:13:23 portabol kernel: [41899.572000] gl860: Iso frame 30 of USB has error -71
Jul 20 00:13:23 portabol kernel: [41899.572000] gl860: Iso frame 31 of USB has error -71
Jul 20 00:13:23 portabol kernel: [41899.576000] usb 1-7: USB disconnect, address 7
Jul 20 00:13:23 portabol kernel: [41899.576000] gl860: isoc_handler() called with status -108 [Plus de Endpoint (altset=0?)].
Jul 20 00:13:23 portabol kernel: [41899.576000] gl860: Error (-19) re-submitting urb in gl860_isoc_handler:1.
Jul 20 00:13:23 portabol kernel: [41899.580000] gl860: isoc_handler() called with status -108 [Plus de Endpoint (altset=0?)].
Jul 20 00:13:23 portabol kernel: [41899.580000] gl860: Error (-19) re-submitting urb in gl860_isoc_handler:1.
Jul 20 00:13:23 portabol kernel: [41899.584000] gl860: Genesys USB2.0 Camera disconnected
Jul 20 00:13:23 portabol kernel: [41899.584000] gl860: Disconnected while webcam is in use !
Jul 20 00:13:26 portabol kernel: [41902.196000] gl860: usb_set_interface failed !

I got 5 ot 6 times the "Unable to capture etc" with camorama and in the syslog there are these messages. I got them everytimes while rotating the webcam. Hopefully, there is not always a problem when I rotate the webcam.
It is possible that because of several rotations there is now an electrical issue in the contact between my laptop and its webcam. Thus that problem may be different from yours if you don't have these messages.

---

### Post by soro2005 on 2008-07-20
Yes, I got a lot of those while experimenting with 0.2n5d. With the newest version 0.2n5e, I have a bunch of them from one go with Skype. Other than that, it looks like it's sometimes, and sometimes not. On that particular go, Skype has had me upside down. Skype does not always start upside down, and for another time when I had it upside down, I cannot find the error -71. The following is grep timestamp (not filtered by anything else), and I don't seem to have the isoc_handler stuff.
```
Jul 20 00:52:31 soro kernel: [  817.552154] gl860: Demande de la taille 320x240
Jul 20 00:52:31 soro kernel: [  817.590415] gl860: Iso frame 19 of USB has error -71
Jul 20 00:52:31 soro kernel: [  817.590429] gl860: Iso frame 22 of USB has error -71
Jul 20 00:52:31 soro kernel: [  817.590433] gl860: Iso frame 24 of USB has error -71
Jul 20 00:52:31 soro kernel: [  817.590440] gl860: Iso frame 29 of USB has error -71
Jul 20 00:52:31 soro kernel: [  817.590443] gl860: Iso frame 31 of USB has error -71
Jul 20 00:52:31 soro kernel: [  817.594408] gl860: Iso frame 2 of USB has error -71
Jul 20 00:52:31 soro kernel: [  817.594417] gl860: Iso frame 4 of USB has error -71
Jul 20 00:52:31 soro kernel: [  817.594424] gl860: Iso frame 9 of USB has error -71
```

This starts with some level of predictability with a full image at 1600 x 1200, although upside down, and it whitebalances itself quickly from relatively true colors to a heavy blue tinge. That's different from what I've seen before, which was a heavy blue tinge from the start on the upside down resolutions. Between 1600 x 1200 and somewhere around 800 x 600 I seem to be getting mostly small b/w inside the big frame. And from 800 x 600 downward, it's starting upside down + blue versus correct orientation + color at what feels like a ratio of roughly 50:50

Sorry if this is all a little confuse. All in all, this one's the one I like most of all I've seen so far. It comes up quick again, and it feels like it's close to getting a handle on the big resolutions as well. Of course, hulkie and blazercist always seem to be left out when it's getting snazzy here. :lolflag:

Oops, this was 1600 x 1200 right orientation and colors right there. Too bad my screen only does 1280. :mad: That looks bigger than real. Only once in >20 attempts, though.

---

### Post by nol_faich on 2008-07-20
My smile comes back! 
Have you tried to rotate your webcam, the image must change its orientation once the webcam looks back the screen. If the image is upside down in front view and in back view, it means that I have to change the basical orientation.

Your error -71 is different from mine because not all frames are concerned, that is why you don't have the disconnect. So in my case I have a mechanical problem with the webcam-laptop link.
Malmostoso had these errors before changing the bandwidth. That change is now done in all version, thus there is still something to understand. I will go back in logs.

Can you try aMsn or Xawtv to test if resizing is OK for you now?

---

### Post by hulkie on 2008-07-20
It works!! 

the version 0.2n5e works without replacing anything. The camera comes on in 1 go for 800x600, 640x480 and 480x360 (does not ask for 640x480 first anymore) and the image is perfect! Brilliant, you fixed the regression.

In dmesg, I now have a different error message:
 gl860: La palette demandee VIDIOCSPICT : 4 (r2_4 r3_5 u_9 y_8)
This is the first time, I have had this message.

In 1280x960; I had the upside down blue image again, switching with the multiple gray small images. But in dmesg, no additional errors (except frame buffer overflow and vidiocspict)

In 1600x1200; I occasionally got a good image, but otherwise the same error messages and wrong images.

I also noticed that the blue light doesn't switch on for the two larger modes, while it works correctly for the smaller modes. Another remark, when I try the shakedown script when the image is blue/grey tilted, the following error messages occur:
gl860: ctrl transfer failed -110 [pffffffc0 r2 v0000 i0000 lg1]
gl860: ctrl transfer failed -110 [p40 r3 v7a00 i0033 lg3]


Anyway, wonderful work!
Happy Hulkie.

---

### Post by nol_faich on 2008-07-20
@ Hulkie and Soro2005
About the upside down state, I need to know if the image is upside down when the webcam looks in front of screen AND behind the screen. To be tested in 800x600 or 640x480.

I don't know what to think about the "gl860: ctrl transfer failed -110 [pffffffc0 r2 v0000 i0000 lg1]". It means that the driver was not able to read in which direction the webcam is looking. As the duration of the driver is 0.4s, I don't know whether the driver was idle for 0.4s or not. Can you tell me Hulkie if the image was locked at the time of error ?

If I well understand, the LED is switched off when you are in 1280x960 and 1600x1200 and there is no error. Is it the same for you Soro2005?


Because of driver version concerns, I log again some informations.

---

### Post by soro2005 on 2008-07-20
Re rotation: Do you mean physically rotate? It seems to me that there is a play of perhaps 45 degree, nothing more. It doesn't feel like it turns backward, but I don't want to try too hard and break it. Perhaps there's a lock somewhere that I haven't found?

I will try with Xawtv now. Just to make sure: The target for resizing is by dragging the window corner? I have opened camorama in all sorts of resolutions, and it opens fine without the black margin that was there before. Not sure it always opens in all the resolutions I request, or whether it just defaults to the next good one.

The shakedown script doesn't seem to be doing anything now. But perhaps I'm overlooking something there. More in a few minutes.

---

### Post by soro2005 on 2008-07-20
Xawtv:
```
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.24-19-generic)
xinerama 0: 1280x800+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
v4l2: read: rc=331776/size=442368
v4l2: read: rc=389376/size=519168
v4l2: read: rc=389376/size=519168
v4l2: read: rc=451584/size=602112
v4l2: read: rc=451584/size=602112
```
That is resizing step by step by dragging the window open. It takes a little time when changing from one size to the next one, perhaps three cycles of the blue light going on and off twice, but eventually fills out the larger frame. I think that this is the dmesg output that corresponds with the last two changes of size:
```
[ 4849.205246] gl860: Demande de la taille 384x288
[ 4856.817406] gl860: Frame buffer overflow (307840/307200)!
[ 4856.889365] gl860: Frame buffer overflow (307412/307200)!
[ 4856.961321] gl860: Frame buffer overflow (307319/307200)!
[ 4868.231148] gl860: La palette demandee : v2 34524742 (r23_33424752 34424752 - b23_33524742 34524742 - uy_59565955 56595559)
[ 4868.256731] gl860: Demande de la taille 416x312
[ 4869.166569] gl860: Frame buffer overflow (307840/307200)!
[ 4875.639001] gl860: Frame buffer overflow (307303/307200)!
[ 4875.942842] gl860: Frame buffer overflow (308480/307200)!
[ 4876.014800] gl860: Frame buffer overflow (308480/307200)!
[ 4876.086758] gl860: Frame buffer overflow (308132/307200)!
[ 4876.663439] gl860: La palette demandee : v2 34524742 (r23_33424752 34424752 - b23_33524742 34524742 - uy_59565955 56595559)
[ 4876.691426] gl860: Demande de la taille 416x312
[ 4884.039378] gl860: Frame buffer overflow (307840/307200)!
[ 4885.088365] gl860: La palette demandee : v2 56595559 (r23_33424752 34424752 - b23_33524742 34524742 - uy_59565955 56595559)
[ 4885.115355] gl860: Demande de la taille 416x312
[ 4885.189741] gl860: Frame buffer overflow (307840/307200)!
[ 4892.469703] gl860: Frame buffer overflow (308480/307200)!
[ 4892.773543] gl860: Frame buffer overflow (307746/307200)!
[ 4892.845501] gl860: Frame buffer overflow (308804/307200)!
[ 4892.917458] gl860: Frame buffer overflow (308127/307200)!
[ 4960.672096] gl860: La palette demandee : v2 34524742 (r23_33424752 34424752 - b23_33524742 34524742 - uy_59565955 56595559)
[ 4960.696258] gl860: Demande de la taille 416x312
[ 4960.768000] gl860: Frame buffer overflow (307306/307200)!
[ 4968.071971] gl860: Frame buffer overflow (308480/307200)!
[ 4968.375811] gl860: Frame buffer overflow (307414/307200)!
[ 4968.447766] gl860: Frame buffer overflow (308480/307200)!
[ 4968.519730] gl860: Frame buffer overflow (307840/307200)!
[ 4969.095131] gl860: La palette demandee : v2 34524742 (r23_33424752 34424752 - b23_33524742 34524742 - uy_59565955 56595559)
[ 4969.127105] gl860: Demande de la taille 416x312
[ 4977.527932] gl860: La palette demandee : v2 56595559 (r23_33424752 34424752 - b23_33524742 34524742 - uy_59565955 56595559)
[ 4977.595087] gl860: Demande de la taille 416x312
[ 4984.969647] gl860: Frame buffer overflow (307785/307200)!
[ 4985.273487] gl860: Frame buffer overflow (307840/307200)!
[ 4985.345442] gl860: Frame buffer overflow (307840/307200)!
[ 4985.417400] gl860: Frame buffer overflow (308480/307200)!
[ 4986.005106] gl860: La palette demandee : v2 34524742 (r23_33424752 34424752 - b23_33524742 34524742 - uy_59565955 56595559)
[ 4986.032801] gl860: Demande de la taille 448x336
[ 4993.376005] gl860: Frame buffer overflow (308480/307200)!
[ 4994.391717] gl860: La palette demandee : v2 34524742 (r23_33424752 34424752 - b23_33524742 34524742 - uy_59565955 56595559)
[ 4994.419700] gl860: Demande de la taille 448x336
[ 4994.521375] gl860: Frame buffer overflow (307567/307200)!
[ 5002.045207] gl860: Frame buffer overflow (307840/307200)!
[ 5002.113196] gl860: Frame buffer overflow (307840/307200)!
[ 5002.185151] gl860: Frame buffer overflow (307840/307200)!
[ 5002.791415] gl860: La palette demandee : v2 56595559 (r23_33424752 34424752 - b23_33524742 34524742 - uy_59565955 56595559)
[ 5002.823646] gl860: Demande de la taille 448x336
[ 5002.877752] gl860: Frame buffer overflow (307840/307200)!
[ 5010.037816] gl860: Frame buffer overflow (307807/307200)!
[ 5027.304359] gl860: La palette demandee : v2 34524742 (r23_33424752 34424752 - b23_33524742 34524742 - uy_59565955 56595559)
[ 5027.331636] gl860: Demande de la taille 448x336
[ 5028.338695] gl860: Frame buffer overflow (307840/307200)!
[ 5035.730544] gl860: La palette demandee : v2 34524742 (r23_33424752 34424752 - b23_33524742 34524742 - uy_59565955 56595559)
[ 5035.758516] gl860: Demande de la taille 448x336
[ 5043.379398] gl860: Frame buffer overflow (308480/307200)!
[ 5043.451386] gl860: Frame buffer overflow (307767/307200)!
[ 5043.523317] gl860: Frame buffer overflow (308480/307200)!
[ 5044.206931] gl860:  ** 7b8d (0) **
```

With regard to your last question: My LED always comes on at all resolutions, also with scrambled images and when it is upside down.

---

### Post by nol_faich on 2008-07-20
If you think you can't return the webcam, you're right to not force. I rotate my webcam several times without watching images and it disconnect one times, this definitively confirm I have a mechanical issue. However I implement the return of the webcam on request of a S37S owner.

_The webcam only knows 4 resolutions : 640x480, 800x600, 1280x960 and 1600x1200._
By just keeping 1 pixel out of 2, 3, 4, etc horizontally and vertically, you 320x240 and smaller resolutions than 640x480.
Before the driver took the biggest resolution less or equal to the requested one and add a black frame to fill the request. Now I take the smallest known resolution greater or equal to the request and I interpolate. If you tried different resolution with camoraman it is OK.

Xawtv is not the easiest soft to use. I tried to skip the size change request when it ask for the same size as before but this freezes Xawtv.

I add a 0.2n5e2 with a shorter delay (6ms instead of 16) and the inversion of the image.
Please let me know if the image is no more upside down and if this is stable in sizes<=800x600 by making several viewer starts/stops and size changes.

---

### Post by soro2005 on 2008-07-20
This one is upside down at all resolutions, and small b/w frames within the big one at 1280x960 and and 1600x1200. It starts like a rocket. :)

---

### Post by accepttheownage on 2008-07-20
First off, thank you for putting in the time and effort into this project, I own a C90S and I'm glad all of my hardware is almost fully compatible!!
Regarding the upside down image, it occurs in every resolution for me, in any orientation (front and back). I notice that when I rotate it fast from back to front it will show my face correctly for a split second, then flip it back to upside down. I'm looking forward to the next release :)

---

### Post by nol_faich on 2008-07-20
Please return to n5e. I was told that the latest version freezes the system sometimes in big size, moreover the image is not inverted.

If the image is upside down with the n5e, please launch monusb while you are watching the webcam and wait 10 seconds before killing monusb. Follow the instruction given by monusb and post the file. I need to know if there is not a concern with the tag to inform us if the webcam looks back or not.
The n5e images are reported to be straight with an Asus S37S which allow the webcam to look back. Maybe not all S37S are able to do that and the read information is meaningless.

---

### Post by soro2005 on 2008-07-20
Here you go. I get a straight image at lower resolutions, only the larger ones are upside down, and sometimes the gray small frames within the large frame. So this is at 1600x1200. 0.2n5e, flavor a, of course.

---

### Post by nol_faich on 2008-07-20
Can you reinstall the driver, try to watch in 1280x960 and once the image is scrambled to give me the "grep gl860 /var/log/syslog" (not the dmesg, because often there is a lack of logs).

---

### Post by soro2005 on 2008-07-20
This is installation + three starts at 1280 x 960. The first two starts were upside down, and the third (last) start was gray small images inside the big frame. I think it looks pretty much identical.

---

### Post by hulkie on 2008-07-21
Hey,

first of all, my webcam doesn't rotate 180° as well. I can tilt it +-15° max. In the lower resolutions up to 800x600 the image is the right way up. Yet, at 1280 and 1600, I often get a blue upside down image. In syslog, I then get additional errors like:
[ 4523.599641] gl860: Iso frame 27 of USB has error -75
[ 4523.599649] gl860: Iso frame 28 of USB has error -71
I tried the shakedown script a couple of times, and even in 800x600, he sometimes doesn't listen to the hflip/vflip commands and then gives the same control errors as I stated in my last post. This doesn't happen every time though, just occasionally.

Then, about the timeouts, I could try to tune them myself, to see what the minimum is that still works. For this, I suppose I should just modify the msleep timeouts in gl860-dev-0503a.c? I will try to reduce them as much as possible and report my values.

Finally, about the blue light; yes, at 1280x960 and 1600x1200 the light doesn't come on, although an image is shown. At the lower resolutions, the light comes on at the correct time.

Hulkie.

---

### Post by hulkie on 2008-07-21
Hey,

I already did those tests. Previously, camorama would start up in 10 seconds. I was able to decrease this to 3 seconds, which is a fair startup time I suppose for a webcam. 
First I decreased all the msleep values in the dev-0503a file down to 10 but this did not decrease the startup time. This is mainly determined by the msleep value in usb.c. Here, I was able to decrease the msleep(16) down to msleep(1) without any startup problems. This gave a startup time of 3 seconds. Fantastic!

While I did not yet notice any problems due to this, I must say that the shakedown script seems to behave more erratic. As I do not need to flip the webcam in skype, a quicker startup seems better, but I will try some other values, and see at which point the shakedown works correctly again.

Hulkie.

---

### Post by nol_faich on 2008-07-21
@ Hulkie : The main sleep time is in fct_RTx as the driver need to send some 600 instructions to the webcam and that in dev-0503a there is less than 20 msleep.
If you do not have more -110 errors with 1ms msleep than with 16 ms, it is OK. But if there is more often errors, this means that sometimes the initialisation will be bad or settings will have no effects. What you can test, is to change settings with camorama (color, brightness and so on) and try to see if there is dependancy between -110 errors and fct_RTx's msleep duration (shorter implies more errors?).
Once the driver was reported to work with 6ms, but not for all everybody. 

@ Soro2005 : really amazing, no transfert error at all. All seems to be understood but this not work. There is a tester who had good big size images with a previous driver version and now the same problems as you. I will try with him to see what causes that behaviour change and what can be the reason why it worked with him and not you.
Also, does the LED switch on when you are in 1280x960 or 1600x1600 ?

@ All : Do not use big sizes more than some second because I was reported system freezes. This was not always the case and it appear in 1024x768 with ids azn interpolation from the 1280x960 webcam mode.
It should be to good to have several msleep testers (read Hulkie part).

---

### Post by nol_faich on 2008-07-21
0.2n6 online : if big sizes do not work and what there is no error, it may be some bad thing transmetted and I find two thing to correct.
Please test with camorama in 1280 and 1600.

---

### Post by soro2005 on 2008-07-22
This one is installation on 0,2n6, one start at 1280, two starts at 1600. The one at 1280 gave gray small frames within the large frame, the two at 1600 were completely scrambled (i.e. noisy lines, no recognizable image). It is also upside down from 800x600 downward.

Re LED: I think my blue led always comes on, regardless of how scrambled the image is. I don't think I've ever had a single try without the blue light coming on. This is definitely a non-issue here. :confused:

---

### Post by nol_faich on 2008-07-22
Sometimes the <=800x600 are upside down and other times not?

---

### Post by soro2005 on 2008-07-22
> **nol_faich said:**
> Sometimes the <=800x600 are upside down and other times not?

No, always upside down (some twenty attempts).

---

### Post by nol_faich on 2008-07-22
0.2n6b online, straight images. I forgot to correct that from the 0.2n5e2 :(

---

### Post by soro2005 on 2008-07-22
Hmm, 0.2n6b is still upside down here. But I have the impression that the colors are better here. All resolutions upside down, and 1280X960 small gray frames inside the big one. 1600x1400 seems to start most of the time with a full image, although upside down and too blue. Attached the syslog of installation and starts at several sizes. The first are 800x600 and 640x480, and although they look very different in the log, they both were upside down.

---

### Post by Jan Olieboer on 2008-07-22
Hi Nol,

Fantastic! the gl860_0.2n6b driver seems quite stable. In the higher resolutions, the image appears a bit blue-ish, and the image is in all resolutions upside down. Here's what I get in my messages file (dmesg | grep gl860).

Cheers,
Jan.

---

### Post by nol_faich on 2008-07-22
0.2n6c. I made a mistake in the correction of upside down, it was only half corrected.

@ Jan : that is wuite a good news, however there still problem, in the big size we are in constant overflow and that is not due to an end-of-image marker issue as bad marker should appear in the log. Is there in the bottom or the top of the image one or several lines which seems to be shifted so that they must be at the opposite horizontal side?
I make a "d" version which logs each end-of-image marker received and the number of bytes received between these marker. Once it is only, I edit this post.

@ all the C90's owner : Please test the 0.2n6c (or d if online)

EDIT : Version "d" online. Test 10 seconds in 1280x960 and 1600x1200. Mail me the "dmesg | grep gl860". Thanks

---

### Post by soro2005 on 2008-07-22
This is still upside down at 800x600, and very scrambled at 1280 and 1600. It is straight (right side up) at 640x480. Talking about 0.2n6d. At 800x600, I can clearly see one or two lines or so at the bottom of the image that are not in sync.

Here is 800x600 (upside down), and attached the dmesg for the two bigger sizes. I don't know how to send you an email, sorry.
```

[36294.016138] gl860: Demande de la taille 800x600
[36294.177740] gl860: taille inter marqueur = 307200 (2)
[36294.369633] gl860: taille inter marqueur = 307200 (2)
[36294.917335] gl860: taille inter marqueur = 307200 (2)
[36295.644919] gl860: taille inter marqueur = 307200 (2)
[36295.916770] gl860: taille inter marqueur = 307200 (2)
[36296.520432] gl860: taille inter marqueur = 307200 (2)
[36296.848254] gl860: taille inter marqueur = 307200 (2)
[36297.639821] gl860: taille inter marqueur = 307200 (2)
[36298.107558] gl860: taille inter marqueur = 307200 (2)
[36298.159528] gl860: taille inter marqueur = 0 (2)
[36298.567301] gl860: Frame buffer overflow (480553/480000)!
[36299.107014] gl860: Frame buffer overflow (480529/480000)!
[36299.294936] gl860: Frame buffer overflow (481670/480000)!
[36299.678700] gl860: Frame buffer overflow (481879/480000)!
[36299.753185] gl860: La palette demandee VIDIOCSPICT : 4 (r2_4 r3_5 u_9 y_8)
[36299.753432] gl860: La palette demandee VIDIOCSPICT : 4 (r2_4 r3_5 u_9 y_8)
[36299.870603] gl860: Frame buffer overflow (480969/480000)!
[36299.870611] gl860: taille inter marqueur = 2406400 (2)
[36300.062488] gl860: taille inter marqueur = 478400 (2)
[36300.254380] gl860: taille inter marqueur = 478400 (2)
[36300.446266] gl860: taille inter marqueur = 478400 (2)
[36300.638155] gl860: taille inter marqueur = 478400 (2)
[36300.826081] gl860: taille inter marqueur = 478400 (2)
[36301.017965] gl860: taille inter marqueur = 478400 (2)
[36301.209868] gl860: taille inter marqueur = 478400 (2)
[36301.401758] gl860: taille inter marqueur = 478400 (2)
[36301.593648] gl860: taille inter marqueur = 478400 (2)
[36301.785536] gl860: taille inter marqueur = 478400 (2)
[36301.977422] gl860: taille inter marqueur = 478400 (2)
[36302.169314] gl860: taille inter marqueur = 478400 (2)
[36302.357247] gl860: taille inter marqueur = 478400 (2)
[36302.549131] gl860: taille inter marqueur = 478400 (2)
[36302.741021] gl860: taille inter marqueur = 478400 (2)
[36302.932911] gl860: taille inter marqueur = 478400 (2)
[36303.124798] gl860: taille inter marqueur = 478400 (2)
[36303.316690] gl860: taille inter marqueur = 478400 (2)
[36303.508577] gl860: taille inter marqueur = 478400 (2)
[36303.700466] gl860: taille inter marqueur = 478400 (2)
[36303.888387] gl860: taille inter marqueur = 478400 (2)
[36304.080284] gl860: taille inter marqueur = 478400 (2)
[36304.272173] gl860: taille inter marqueur = 478400 (2)
[36304.464073] gl860: taille inter marqueur = 478400 (2)
[36304.655965] gl860: taille inter marqueur = 478400 (2)
[36304.847852] gl860: taille inter marqueur = 478400 (2)
[36305.039758] gl860: taille inter marqueur = 478400 (2)
[36305.227660] gl860: taille inter marqueur = 478400 (2)
[36305.419553] gl860: taille inter marqueur = 478400 (2)
[36305.611443] gl860: taille inter marqueur = 478400 (2)
[36305.803333] gl860: taille inter marqueur = 478400 (2)
[36305.995223] gl860: taille inter marqueur = 478400 (2)
```

---

### Post by nol_faich on 2008-07-23
The image should be straight for at least 640x480 and 800x600. The 0.2n6c and d were tested yesterday and the one who made the test does not report upside down image in these resolutions.
After each received image, I read from the webcam a value which indicates whether it is returned or not. As your S37S model does not allow to return the webcam, maybe the read value has no sense and that sometimes I read something which means image to be inverted or image straight. I will add the read value in the logs.

---

### Post by Jan Olieboer on 2008-07-23
Hi Nol,

Tried the 0.2n6d version, and again, quite stable in 800x600, but still upside down. The resolutions 1280x960 and 1600x1200 were not stable ,and the image was running over the screen. Attached you'll find the dmesg|grep gl860 output. I use the c-version of this driver.

Cheers,
Jan.

---

### Post by hulkie on 2008-07-23
Hey Nol,

for my camera things have improved as well, at 1280 and 1600 the blue light comes on now (I tried the 0.2n6e with default timings, I'll adjust them later). Yet, the result stays the same, I have or little grey images or an upside down blueish image. Interestingly, in the logs they are different as well; for the grey images there is no inter marker found, whereas for the upside down image, the inter marker is found. 
I also included the log of an 800x600 session as a reference. For this resolution and 640x480 the image was the right side up for me (also c version). Perhaps my webcam or that of Jan is mounted the wrong way around? Perhaps Jan could try the shakedown script and see if this is able to invert his image for resolutions up to 800x600. For me, this script works up to 800x600, after this, the hflip and vflip commands do not work anymore (while the lum=Max and such continue to work strangely enough...). I would say that if he can invert his image with the script, that this is just a different default setting, not the same problem as I experience starting from 1280x960.

Hopefully the logs will help you.
Hulkie

---

### Post by nol_faich on 2008-07-23
@ Jan : the only difference between the 6b which works for you at all sizes (except the upside down images) and the 6d is the fix for upside down and a new information logged. Nothing less, nothing more. Try 800x600 then 1600x1200 with the 6d and if it does not work in big size reinstall the 6b (still online, no laptop restart) and try 800x600 then 1600x1200. If the later driver works, it's a miracle.

I uploaded a "n6e". It is "n6d" with a new logged information about upside down image. You test all sizes (640x480, 800x600, 1280x960, 1600x1200) 4 seconds and you post then "dmesg | grep gl860".


@ Hulkie : have you small images at the beginning and after some seconds bluish images. Could you post a snapshot of the bluish image?

@ all : what I learned from the "6d" :
* you don't have a very 800x600 but a mere 800x598 (however it is absolutely not useful to ask for 800x598, don't care about that, continue to use 800x600). We never get the last 2 lines in the bottom of images. The first bottom line is zeroed by the debayerisation process, the second line in the bottom shows anything. I will set it to 0.
From Hulkie log, the 1600x1200 is a mere 1600x1198. 1280x960 is 1280x1024 (not a 4/3 format) and we will be always in overflow as we receive more pixel than expected! I love the 0503!
* the second thing is that when you go from 800x600 to 1600x1200, we receive at a lower framerate 800x600 images until the end of the webcam reinitialization (takes some seconds), that is the small images in the big ones : we ask 1600x1200 but we still receive 800x600 so we fill a 1600x1200 with the smaller ones. Due to an unknown reason, there is a one pixel shift each new line, this is why the small picture are tilted.
* in big size, once the initialization is finished, we get no more end-of-image marker, this is why we are constantly in overflow (observed with two S37S, but Hulkie with its C90 does not have that).

Can someone with a Windows test that with the webcam viewer the small images are included in the big ones?

---

### Post by nol_faich on 2008-07-23
0.2n7 online. EXPERIMENTAL verison which handles 1280x1024 instead of 1280x960 for the C90/S37S sensor.
camorama -x 1280 -y 1024
if this works, try :
camorama -x 800 -y 640
and compare with :
camorama -x 800 -y 600
Do both last images have the same field of view or not ?
If the field of view is the same, the 1280x1024 images should be vertically a little bit stretched.

---

### Post by soro2005 on 2008-07-23
with 0.2n7:
 - 1280x1024 is mostly upside down, and sometimes there's the small frames inside large frame one. It looks like your description might explain what's going on, although I don't need to start the camera in a lower resolution first to get the small frames inside large frame version. When upside down, the image in fact turns blueish after a couple of seconds. The small frames inside large frame one is mostly upside down, but I've also seen it at least once right side up. Sometimes it starts like the first shot below, mostly to then transition to small frames within large frame.
 - 1600x1200 is similarly, only that it seems that the small+gray inside large frame is more frequent here.
 - 800x640 is the same as 800x600, only with black bars on top and bottom and one row at the bottom which flickers.
 - 800x600 is mostly right side up, but sometimes upside down, and it now has a black horizontal line across the middle.
 - 640x480 is fine.

---

### Post by nol_faich on 2008-07-24
The black bar is certainly an error as I do not have zeroed the good lines.
Your dmesg is unusable bacause of a lot of -71 errors. So I need the /var/log/syslog. If you see sometimes an image right up, the dmesg at that moment is important because it will allow me to see if we received a different information from the webcam about the image orientation.
Edit : the 800x640 did not work, it should have been a resizing of the 1280x1024, which is not the case.
It is possible that small images appear in the big ones in case of direct start in 1280x960 or 1600x1200 if the webcam send data in 640x480 or 800x598 until it is initialized, a kind of default format until it knows what to send.

@ Hulkie : if the image is scrambled in big size, the hrz/vrt flip effect may be impossible to see. If when the image is good (blueish) it does not work, it maye be interesting to log in Windows the hrz/vrt flip for while you are in big size.
Can you also make a screenshot of the raw data in big size when the image is blueish. To make this use the command line for mplayer, change the size to be 1280x960 or 1600x1200 and change fmt to be "y8" instead of "rgb24". It is possible that a different colorspace is used if the image is to blue.

---

### Post by nol_faich on 2008-07-24
@ all

Could you post the result of the command line:
lshal | grep "system.product"

The result may be used to automatically choose the driver if the answer is stable enough. It is in particular very important for Asus barebones to see if the original model is precised.

---

### Post by soro2005 on 2008-07-24
> **nol_faich said:**
> @ all

Could you post the result of the command line:
lshal | grep "system.product"

The result may be used to automatically choose the driver if the answer is stable enough. It is in particular very important for Asus barebones to see if the original model is precised.

I don't have system.product, but

system.hardware.product = 'S37S'  (string)

I will try to produce better logs later today.

---

