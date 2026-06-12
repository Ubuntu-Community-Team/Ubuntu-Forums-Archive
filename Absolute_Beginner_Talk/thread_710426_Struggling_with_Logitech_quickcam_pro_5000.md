---
title: "Struggling with Logitech quickcam pro 5000"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by ubername on 2008-02-28
Hi

I have looked at many places on the web, forums, google etc. but cannot get my Logitech Quickcam pro to work.

I have (apparently successfully) built and installed the UVC driver. I have downloaded ekiga and tried the setup - interestingly I got the error message 'error with the frame size'


Canorama says 'could not connect to device dev/video0'

lsusb gives (amongst other things) 
Bus 007 Device 007: ID 046d:08c5 Logitech, Inc. 
Which is the camera I believe

dmesg gives (amongst other things)

[  141.135608] usb 7-4.3: new high speed USB device using ehci_hcd and address 5
[  141.419129] usb 7-4.3: configuration #1 chosen from 1 choice
[  141.584855] Linux video capture interface: v2.00
[  141.854687] usbcore: registered new interface driver snd-usb-audio
[  141.855841] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c5)
[  141.869019] usbcore: registered new interface driver uvcvideo
[  141.869270] USB Video Class driver (SVN r189)
[  151.459315] uvcvideo: Failed to query (130) UVC control 7 (unit 2) : -32 (exp. 2).

Can anyone help?

TIA

---

### Post by TeoBigusGeekus on 2008-02-28
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")
Your cam is located near the middle. Good luck!

---

### Post by pogo69 on 2008-03-04
I still can't get camorama to work with my quickcam pro 5000, but I really don't care about that... I have, however, successfully shared webcam via aMSN, using the latest release of aMSN and the svn of uvcvideo.

I've subsequently tried to get ekiga going, but it didn't work out of the box (using what I think was the release available via package manager), until I realised (read somewhere) that it will only work with V4L2, not the default installed V4L.

so... if you haven't already done so, go to the ekiga site, and download the ubuntu distribution of the V4L2 plugin:

[http://www.ekiga.org/admin/downloads/latest/ubuntu/feisty-i386/libpt-1.10.10-plugins-v4l2_1.10.10-2~feisty~ekiga.4575_i386.deb]("http://www.ekiga.org/admin/downloads/latest/ubuntu/feisty-i386/libpt-1.10.10-plugins-v4l2_1.10.10-2~feisty~ekiga.4575_i386.deb")

you'll find a shared library in there somewhere that needs to be installed into the pwlib plugin directory somewhere (the instructions are in the download).

good luck... and be persistent...

cheers,

--pogo (pat)

---

### Post by ubername on 2008-03-05
> **pogo69 said:**
> I still can't get camorama to work with my quickcam pro 5000, but I really don't care about that... I have, however, successfully shared webcam via aMSN, using the latest release of aMSN and the svn of uvcvideo.

I've subsequently tried to get ekiga going, but it didn't work out of the box (using what I think was the release available via package manager), until I realised (read somewhere) that it will only work with V4L2, not the default installed V4L.

so... if you haven't already done so, go to the ekiga site, and download the ubuntu distribution of the V4L2 plugin:

[http://www.ekiga.org/admin/downloads/latest/ubuntu/feisty-i386/libpt-1.10.10-plugins-v4l2_1.10.10-2~feisty~ekiga.4575_i386.deb]("http://www.ekiga.org/admin/downloads/latest/ubuntu/feisty-i386/libpt-1.10.10-plugins-v4l2_1.10.10-2~feisty~ekiga.4575_i386.deb")

you'll find a shared library in there somewhere that needs to be installed into the pwlib plugin directory somewhere (the instructions are in the download).


Yeehaa!


Thanks, I have just got ekiga to recognise my webcam and display a picture of what it is 'seeing' in the ekiga package. It took a bit of work and unplugging then replugging the camera while ekiga was running but it works. That is pretty much what I wanted to prove. I can figure out other stuff as time goes by, or I can raise issues etc. with other software since I now know that the camera CAN work under gutsy. Thanks again. 


good luck... and be persistent...

cheers,

--pogo (pat)

Yeehaa!

Logitech quickcam pro 5000 now works in ekiga on Gutsy. (or at least I think it works - it certainly shows the images the camera is receiving in the video window)

That means I can confidently say that the hardware / driver / O/S work together, it's just a question now of figuring out how to get the other software to work.

Thanks

---

### Post by ubername on 2008-03-05
Whoops - I seem to have posted inside and outside the Quote. Sorry about that

---

