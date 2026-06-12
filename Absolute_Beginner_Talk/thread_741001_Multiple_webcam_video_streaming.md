---
title: "Multiple webcam video streaming"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by JonFarrimond on 2008-03-31
Hello,

I'm not too sure where I should have placed this post since it crosses multimedia, x64, dell support and beginner support. So I thought I was less likely to get beaten about the upper body here.

The background to my problem is that for the research I do I need to setup multiple webcam streams observing 12 locations where events may occur. Hence I've installed Ubuntu 7.10 and zoneminder ([http://www.zoneminder.com/]("http://www.zoneminder.com/")), both of these function well. My problem is that when I try to use more than one webcam at any one time the gspca driver can't cope as both the webcams are identical and therefore have the same software identifiers. 

Logically this must be possible otherwise projects such as zoneminder would never get started. Does anyone have any ideas whether it is a good idea to try to alter the software identifers associated with the devices in the gspca driver files or know of other webcam drivers that are able to differentiate between different identical webcams?

I really don't fancy coding this myself as I would tend to go down the poling individual device locations in turn which would get very messy very quickly and my C# coding isn't what it used to be.

Thanks in advance.

---

### Post by Joe Beam on 2008-03-31
Did you define the different device locations /dev/video0 /dev/video1 in the zoneminder configuration?

Are you saying you did that for zoneminder and the gspca driver is getting confused?

I've never used ZoneMinder but I do use Motion with the gspca driver.

---

### Post by JonFarrimond on 2008-04-01
Thanks for the reply.

The problem is with the gspca driver, not zoneminder. 

It is possible to view either webcam independently of the other in any of my computers USB ports both in camorama and zoneminder.

The problem only arises when two or more identical webcams are plugged in at the same time.

---

### Post by Joe Beam on 2008-04-02
It might be only 1 cam per usb controller. Do you have another webcam you could try? Just to make sure the problem isn't with the cams being identical.

from [http://www.lavrsen.dk/twiki/bin/view/Motion/FrequentlyAskedQuestions#How_do_I_get_Motion_to_work_with](http://www.lavrsen.dk/twiki/bin/view/Motion/FrequentlyAskedQuestions#How_do_I_get_Motion_to_work_with)

USB cameras
    A USB camera uses all the bandwidth a USB1.1 controller can give. Even at low framerates the camera reserves more than half the 11 Mb/s. This means that the 2nd camera gets rejected. Few motherboards have more than one controller. Often 2 or 4 physical connections on a motherboard shares one and the same USB controller. To add more cameras you need to put USB adapter cards. One per camera. There exists cards with full bandwidth per USB socket. These present themselves as for example 4 USB controllers to Linux and they work fine with 4 cameras. Also, many (if not most) cheap PCI USB1/2 cards ($10 range) have a controller capable of supporting 2 x USB1 cameras and an additional USB2 camera per card. With those cards and USB1 extender cards (allowing extension of a USB1 device for up to 100m, typically 50m) you can have a capable surveillance setup using only USB cameras.

---

