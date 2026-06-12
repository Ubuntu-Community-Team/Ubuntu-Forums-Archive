---
title: "luvcview works, why not camorama?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by blippy on 2007-03-16
I'm attempting to do some webcam messaging.  I'm using a Logitech Quickcam Pro 5000. I've compiled and installed the drivers, so when I type 
luvcview
I can see my webcam come up.

I just can't get the webcam to work with any other programs. For example, if I type
camorama
it says "Could not connect to video device (/dev/video0)"
even though it's the one luvcview seems to use.

Alternatively, if I use 
xawtv
I just get a black window.

Anyone know what I need to do?

---

### Post by Jonam on 2007-03-19
Try running camorama from the command line and select the video device as follows:

~$ camorama -d /dev/video0

Do you have two video devices in your PC?

Jonam

---

### Post by blippy on 2007-03-23
Yes, I tried that, but it didn't work.

It complains: "Could not connect to video device (/dev/video0). Please check connection".

If I do
   modprobe -l | grep uvc
I get
   lib/modules/2.6.17-10-generic/usb/media/uvcvideo.ko

I can get my webcam  to work with luvcview, though. luvcview has the following (sufficient) dependencies:
  apt-get install libsdl1.2-dev

OK. here's a link to the wiki page that I created:
   [https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy](https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy)
The good news is that you can take snapshots and record video from it. How to incorporate it with camorama and instant messaging is yet to be determined.

---

### Post by alex-v on 2007-04-15
So far the only two programs that work with the Logitech 5000 pro other than luvcview is aMSN (instant messaging) and ffmpeg (video capture and encoding).

None of the other programs that claim to support the webcam (ekiga, wengophone etc) actually work with it.

My guess is Logitech came up with some kind of hardware upgrade so what we buy as 5000 pro is actually different product from the one used to test (successfully) all those applications. The only hope is the future versions of the driver.

---

### Post by alex-v on 2007-04-15
I have an update - I've gotten ekiga to work (sort of). The solution was to install additional package to support v4l2 driver. The package name is libpt-plugins-v4l2. I wonder why it is not installed by default when one installs ekiga.

I said 'sort of' because I've yet to use ekiga to actually establish videoconference with somebody. All I got so far is the webcam is recognized and I can see my face in ekiga's window. Oh and when I try to use ekiga's testing address sip:500@ekiga.net it connects, the image freezes and I am able to test my audio connection (the pseudo-user basically repeats what you say). But when I disconnect from it so does ekiga from the webcam and I see familiar message that USB device can not be connected to. 

In order to rectify that I have to go through series of restarts of ekiga together with opening aMSN's webcam testing window.

So all in all the only program that works with the 5000 pro more or less reliably is aMSN.

---

