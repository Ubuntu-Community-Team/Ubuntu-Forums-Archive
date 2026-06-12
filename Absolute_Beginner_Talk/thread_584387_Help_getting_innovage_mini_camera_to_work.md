---
title: "Help getting innovage mini camera to work"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by animefan61 on 2007-10-20
Hi, I bought a Innovage mini camera a couple of years ago. I couldn't get it to work on Windows, so I put it up. I found it today and decided to try to install it in Ubuntu. I have the cd and used Wine to install it, and now when I try to open it up it says the drivers open failed. I get the screen but I can't see any pictures. Also none of my digital camera programs recognize it, can someone help me?

---

### Post by ofb on 2007-10-21
Well, support is listed as "experimental"
[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

A little thread here has some signal mixed in the noise,
[http://ubuntuforums.org/showthread.php?t=79243](http://ubuntuforums.org/showthread.php?t=79243)

> Also none of my digital camera programs recognize it
You mean in Ubuntu right? Just want to make sure you're trying it in Ubuntu. I'd skip Wine and the official drivers myself. I find Ubuntu detects fine by itself, even a wretched old Agfa I have. (Also listed as 'experimental'.) The most I've had to do is reboot after installing Camorama to get webcam ability to work with that one, something I'd never managed with the official drivers under Win when the camera was new.

---

### Post by animefan61 on 2007-10-21
Yes, digicam and gtcam won't detect it. I haven't tried Camorama, I'll install it and see if it works. I don't really care about the webcam part, I just want to be able to take pictures and download them to my computer.

---

### Post by ofb on 2007-10-21
I actually don't have digikam and gtkam installed. The default gthumb is what fires up here. But a quick check shows they all use libgphoto2, so I suppose it doesn't matter.

If none of the tips on that other page help, then I'd lean towards suspecting hardware trouble - either the camera or the cable may not work any more.

If you want to try camorama just for fun, then I should mention that with my Agfa I had to leave it plugged in and on while the computer rebooted. 

(Batteries are not required for functioning as a webcam, or for just downloading pictures in the case of my Agfa.)

---

