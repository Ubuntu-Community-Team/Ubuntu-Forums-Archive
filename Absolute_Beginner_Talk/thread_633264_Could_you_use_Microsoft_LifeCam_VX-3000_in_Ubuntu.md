---
title: "Could you use Microsoft LifeCam VX-3000 in Ubuntu?"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by enjtpl on 2007-12-06
I couldn't use Microsoft LifeCam VX-3000 in Ubuntu.

---

### Post by Znort_Ubern00b on 2007-12-06
> figueiravascoApril 30th, 2007, 04:12 PM
There's an update at [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) and there's also explicit reference to this webcam. I don't know if it works, but I think it worths a try...

try the link it may help you...

> jespdjMay 2nd, 2007, 06:46 PM
I also have a Microsoft LifeCam VX-3000. I downloaded the driver from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Unfortunately there seems to be very little documentation on what to do after downloading this, so I figured it out myself. First I had to unpack it and compile it - that was easy. Just "tar xvfz gspcav1-20070426.tar.gz" to unpack it, then cd to the directory and type make.

This leaves me with a kernel module: gspca.ko

I made a directory "/lib/modules/2.6.20-15-generic/kernel/webcam" and copied the module there, then did "sudo depmod" and "sudo modprobe -v gspca".

This all worked OK and the module was loaded.

I then used camorama to see if it works, and camorama sees the camera but it does not work properly. I get a garbled image, I can more or less see myself but the image is full of red and blue distorted blocks... :(

Also it seems to interfere with my Microsoft wireless USB mouse; the computer does not react to mouse buttons anymore when the webcam is active. Very annoying... :(

Using 64-bit Feisty Fawn.


> jespdjMay 3rd, 2007, 09:38 PM
An update...: I discovered in Windows XP in the Device Manager that my mouse and webcam were on the same USB main hub. My computer has 6 USB ports; four on the back of the machine, two on the front. The webcam and mouse were in connected to two ports next to each other in the back. Apparently that means that they are on the same USB main hub.

I now plugged my webcam into another port and now it doesn't interfere with the mouse anymore.

The image in camorama now looks different, but still completely wrong. I can now see myself, but the image is very dark and the colors are wrong; my face is blue and my shirt is red (which is blue in reality...).


---

### Post by g7kse on 2008-01-18
here is the [whole thread]("http://ubuntuforums.org/showthread.php?p=4162010#post4162010")

there seem to be a number of issues with this webcam. so unless there is anything else then I'm not sure it's a good choice. i have one too and presently it does help us fix it but hopefully a bright spark will find a good answer

---

