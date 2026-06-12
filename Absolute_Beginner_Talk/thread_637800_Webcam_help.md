---
title: "Webcam help"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by AngelAir on 2007-12-11
Hello All!
I am e newbie in Linux (Ubuntu 7.10) and have an installation problem with the web cam.  I have tried everything I have been able to find on the net about web cams and Linux.  My web cam is not been detected.

With the command **lsusb**, I get; Bus 005 Device 003: ID 2770:930b NHJ, Ltd
In **System>Preference>Hardware Information**:  USB 2.0 PC Camera - USB Vendor Specific Interface - /org/freedesktop/Hal/devices/usb_device_2770_930b_noserial_if0

My Cam is a Micro Innovation In-Sight Motion Webcam Model: IC825c

Please HELP!!! :confused:

---

### Post by linuxwizard on 2007-12-11
You might try EasyCam see if it will find a driver for you.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by Dr Small on 2007-12-11
Sorry to hijack this thread, but what would a good webcam that would be supported out of the box, be ? I would like to know, as I wish to get a webcam one day.

Dr Small

---

### Post by linuxwizard on 2007-12-11
Look over these links will give you some ideas

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

### Post by AngelAir on 2007-12-11
Yes I did installed Easycam; but, it did not find the webcam.

---

### Post by AngelAir on 2007-12-11
I also installed spca5xx; since it had work with other Micro Innovation cameras, but it did not work

---

### Post by darthbushi on 2007-12-11
Hello,

I'm an Ubuntu n00b too, and I was wondering whether there is any support for Genius Slim 310NB webcams out there. I own one and since I'm migrating from WinXP I'd like to make it work somehow (I can't stand WinXP anymore!). I checked to see if Ubuntu detected it, but there's no /dev/video0/. Also, I tried using EasyCam, but didn't work. Finally, I tried googling around and had absolutely no luck. Do you have any ideas?

Thanks for your help!!

Oh, and by the way, I'm using Ubuntu 7.10... When I was googling out a solution for my problem, I found this list:
[https://wiki.ubuntu.com/SkypeWebCams?highlight=%28webcam%29](https://wiki.ubuntu.com/SkypeWebCams?highlight=%28webcam%29)
Those are cameras that can be used with skype... It seems like any Logitech webcam would be good for you, Dr Small, since there's good support for them.

Thanks again!!

---

### Post by dim_sa on 2008-02-13
Hello!
I have Genius Slim 310NB camera and it work in my linux. 
I try to explain, that i have made.
1. Download source gspcav1-20071224.tar.gz from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) and unpack archive to gspcav1-20071224 catalog (for example)
2. Edit gspca_core.c in gspcav1-20071224:
        line 818, change '{USB_DEVICE(0x0458, 0x7025)}, /* Genius Eye 311Q sn9c120+Mi360 */' to '{USB_DEVICE(0x0458, 0x702e)}, /* Genius Eye 311Q sn9c120+Mi360 */'
        line 3784 change 'case 0x7025:' to 'case 0x702e:'
        line 3787 change 'spca50x->sensor = SENSOR_MI0360;' to 'spca50x->sensor = SENSOR_OV7660;'
3. Build drivers (see READ_AND_INSTALL in gspcav1-20071224)

And the camera works, BUT with some BUGS: bad colors (white blinks) and inversed image =(
If somebody knows as to correct this problem, write please!

---

