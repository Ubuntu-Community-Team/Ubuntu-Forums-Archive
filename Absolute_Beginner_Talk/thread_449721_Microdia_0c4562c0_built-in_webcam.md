---
title: "Microdia 0c45:62c0 built-in webcam"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by bluemarvel on 2007-05-20
Hello:

I am trying to get my Microdia webcam that is built into my HP Pavilion dv9000 notebook working on Feisty. I'd like to be able record video into software so that I can vlog, like I used to do on OS X using Quicktime Pro.

My webcam works very well under Ekiga 2.0.3 but no other software recognizes it.

Does anyone have any suggestions?

Thanks!
J.P.

*Camstream reports*:
The device experienced an error -19 (No such device).
*With this going on in the console*:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
CVideoDeviceInput: Warning: no channel info available.
CCamWindow::CCamWindow()
CWebCamViewer::CWebCamViewer(0x80d28e0, 320x240)
CVideoDevice::Init()
Allocating own buffer.
Trying to find video options for USB 2.0 Camera:/dev/video0
searching USB 2.0 Camera
CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
CVideoSettingsDlg::SizeChanged(176x144)
CVideoSettingsDlg::FramerateChanged(10)
CCamPanel::SetSize(176x144)
CCamPanel::SetImageSize(176x144)
CCamPanel::SetVisibleSize(176x144)
CVideoDevice::SetSize(320, 240)
CCamPanel::SetSize(320x240)
CCamPanel::SetImageSize(320x240)
CCamPanel::SetVisibleSize(320x240)
CWebCamViewer::DeviceChangedSize(320x240)
RecalcTotalViewSize: resize viewport(320x240)
CCamPanel::SetSize(320x240)
CCamPanel::SetImageSize(320x240)
CCamPanel::SetVisibleSize(320x240)
RecalcTotalViewSize: resize viewport(320x240)
EnableRGB: +
CVideoDevice::SetPalette picked palette 8 [yuyv]
CVideoDevice::CreateImagesRGB()
 allocating space for RGB
CVideoDevice::StartCapture() go!
CVideoDevice::LoadImage() Error loading image; errorcode=-19

EnableRGB: -
CVideoDevice::ResetImagesRGB()
 freeing memory
CVideoDevice::SetPalette picked palette 0 []
CVideoDevice::StopCapture() halt!
CWebCamViewer::~CWebCamViewer()
CWebCamViewer::StopTimeSnap()
CWebCamViewer::StopFTP()
CCamWindow::~CCamWindow()


*lsusb*:
Bus 005 Device 003: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1130:6606 Tenx Technology, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  


*caminfo*:
CVideoDeviceInput: Warning: no channel info available.Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "USB 2.0 Camera"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 0x0
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

---

### Post by bluemarvel on 2007-05-20
bueller? Bueller? Anyone? Bump!

---

### Post by TutoWRM on 2007-06-07
I have the same issue..... the webcam only works under ekiga, but no amsn or any other software, i read that it was because ekiga only supports the v4l2 driver or so....
The most bizzard thing it was, that i get the webcam work on ubuntu edgy and amsn, but i don't know why it won't work under feisty........
i've done everything i can, please someone respond :( i have the same hardware a microdia webcam.

---

### Post by Inxsible on 2007-06-07
Yeah, the built-in cam works only for Ekiga and no other known software yet.

Tutowrm is right about V4L2 drivers that are needed. Only Ekiga has support for those drivers. although if you have ekiga installed, cant you use the same drivers in other software.

Unfortunately, i dont know how to :(

---

### Post by TutoWRM on 2007-06-20
it's gonna sound very, but very lame, but somewhere i've readed that the cam's works just fine out of the box, it's just a few simple steps of "selecting" the camera, in the programs, and all the compiling and stuff, just got'it wrong, and because of that it didn't work, so, in a very deseperate way, i just make a clean install of ubuntu (feisty ) and guess what, i run ekiga and choose my camera and surprise it works, and after installing automatix i installed amsn, and surprise it' worked too, so my guesses are that because of installing the driver i'v f*cked up and that the reason it's didn't work. as i said before, i had tried everythig the ucv, and other stuff with no results. dunno but if you have little to backup or even better if you have your files in a different partition, who knows, reinstalling will sweep of you mess up and you'll be working on a system as a more mature linuxer :D

i'm running a hp dv2225la with integrate camera, dunno i hope it works for you, if you make up your mind, and believe me u'll be running ubuntu as a more mature linuxer :)

---

### Post by buntunub on 2007-07-19
Apparently, this camera works under uvc. There are a smattering of posts about it and a very few have said that it actually works after days of recompiling and reinstalls. The only real promising link ive found about how to actually get the correct sources and compile options ended up being a shut down site. I think since this cam has somehow become classified as "working in linux" by someone, further development on an actual working driver for us probably wont happen until the correct bug reports get filed and the devs get thier hands on one of these particular cams.

---

### Post by ahsid on 2007-08-22
Hi, I have the same webcam, I'd really like to make it work. I've tried out a couple of  french Howtos and it still doesn't work. Still no solution around here?

---

### Post by kornface13 on 2007-08-23
[http://ubuntuforums.org/showthread.php?t=512059]("http://ubuntuforums.org/showthread.php?t=512059")

That thread tells you how to do it exactly.  it worked perfectly for my dv6000 laptop.

---

### Post by ahsid on 2007-09-17
kornface13, I tried  out this post but it didn't work. (I was using feisty at that time) Now I'm using the 2.6.21 kernel with Debian Lenny and this technic still doesn't work... I can see myself by typing :
luvcview -d /dev/video0 -f yuv -s 1280x1024    in the terminal but when I try out kopete I only have a green window in the webcam setttings, the section device says usb2 camera but that's it, I can't change anything.
Amsn doesn't work either, the blue light comes on when I go in the webcam settings and select my usb2 camera but it comes off as soon as I close the window. Then when I try to make it work while talking to someone, the light comes on from time to time but no video appears....
Does someone knows how to make it work either on feisty or debian testing using kopete or amsn??

---

### Post by scorp123 on 2007-11-28
> **ahsid said:**
>  I can see myself by typing: "luvcview -d /dev/video0 -f yuv -s 1280x1024" in the terminal but when I try ... I only have a green window in the webcam setttings, the section device says usb2 camera but that's it, I can't change anything.  Same problem here. I can load the "uvcvideo" drivers, I can compile the newer versions, I can get a picture when I run "luvcview" ... but other than this every other application just shows a completely black (e.g. Skype) or a completely green (e.g. Ekiga) screen and no picture is shown. My situation is described in details here:
[http://ubuntuforums.org/showthread.php?p=3847488#post3847488](http://ubuntuforums.org/showthread.php?p=3847488#post3847488)

I'd really welcome help here. :)

---

### Post by reh4c on 2008-02-18
On Hardy Alpha 4, Cheese 2.21.5 and Ekiga both work with this webcam.  I can't get camorama and gqcam to work.  It appears that Cheese and Ekiga use V4L2 vice V4L.  Could that be the issue?

---

### Post by spiderbatdad on 2008-02-18
easycam is supposed to provide a driver and support for this built-in cam.

---

