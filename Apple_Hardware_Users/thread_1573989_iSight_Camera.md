---
title: "iSight Camera"
date: 2010-09-13
forum: Apple Hardware Users
---

### Post by MegaLoler on 2010-09-13
I have a 2005 mac mini with ppc ubuntu 10.04.  I want to be able to use my external isight camera with it.  Is it possible on a ppc mac?

---

### Post by chaanakya_chiraag on 2010-09-13
Plug it in and see :lol:

---

### Post by chaanakya_chiraag on 2010-09-13
One of two things will happen:
1) The computer will not recognize it.  If this happens, post back and we'll see what we can do.
2) The computer will recognize it.  If this happens, please mark this thread as solved by going to Thread Tools -> Mark as Solved.
You can tell if the camera works by going to a program such as cheese or luvcview (command-line).  If you need help trying to figure out if it works, please post back and we'll help you figure out if it works.

---

### Post by MegaLoler on 2010-09-13
Thanks so much for the quick reply :D
I launched cheese and it said no device found.  When I plug in the camera, the green light lights up for a second and then goes off

---

### Post by chaanakya_chiraag on 2010-09-14
Hmmm...if cheese says "no device found" after plugging in the camera...could you please post the output of ```
lsusb
```  Let's see if the computer recognizes it...it should...
To run the command ```
lsusb
``` open up Terminal (Applications->Accessories->Terminal) and type in the command ```
lsusb
```

---

### Post by chaanakya_chiraag on 2010-09-14
Actually, try the instructions [here]("http://ubuntuforums.org/showthread.php?t=491381")

---

### Post by MegaLoler on 2010-09-14
output:
```
Bus 004 Device 004: ID 05ac:020b Apple, Inc. Pro Keyboard [Mitsumi, A1048/US layout]
Bus 004 Device 003: ID 05ac:0304 Apple, Inc. Optical USB Mouse [Mitsumi]
Bus 004 Device 002: ID 05ac:1003 Apple, Inc. Hub in Pro Keyboard [Mitsumi, A1048]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 009: ID 0763:0150 Midiman M-Audio Uno
Bus 001 Device 008: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 001 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Btw, the isight camera is connected via firewire lol
but anyway, let me try those other instructions now

---

### Post by MegaLoler on 2010-09-14
those instructions didn't work, starting with the second command, no directory found.  I'm guessing because that is for Gutsy, and I have Lucid

---

### Post by chaanakya_chiraag on 2010-09-16
The directory for Lucid (for the second command) is:
```
/lib/modules/$(uname -r)/kernel/drivers/media/video/uvc
```
Therefore, the modified command is:
```
 sudo mv /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko.original
```

---

### Post by chaanakya_chiraag on 2010-09-16
Then, for the apt-get install command, the modified one (for Lucid) is:
```
sudo aptitude install libusb-1.0-0 libusb-dev linux-headers-$(uname -r)
```
The rest *should* be the same...

---

### Post by paulinchen on 2010-09-16
didn't work.

I destroyed my uvcvideo module

Thanks

---

### Post by chaanakya_chiraag on 2010-09-17
Hmmm...what exactly happened?  Does the iSight not even flash green now?

---

### Post by chaanakya_chiraag on 2010-09-17
I mean, you could always do ```
 sudo mv /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko.original /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko
```to restore the original module.

---

### Post by bendog on 2010-10-08
any update on this thread?

---

### Post by chaanakya_chiraag on 2010-10-08
Since I don't have a Mac/iSight, I can't really help...sorry :(  Apparently old instructions do NOT work well, as can be seen by the thread:(

---

### Post by oswaldkelso on 2010-10-08
> **MegaLoler said:**
> I have a 2005 mac mini with ppc ubuntu 10.04.  I want to be able to use my external isight camera with it.  Is it possible on a ppc mac?

Yes it works. I tested mine last month in ekiga under Debian squeeze. unfortunately I'm in the middle of moving so the computer with the webcam is 15 miles away. How ever there is a lot of info here:

[http://ubuntuforums.org/showthread.php?t=572039](http://ubuntuforums.org/showthread.php?t=572039)

[http://ubuntuforums.org/showpost.php?p=4649034](http://ubuntuforums.org/showpost.php?p=4649034)

I didn't do anything quite as complicated. just installed the firewire drivers (1394 modules) set permissions, and set up the camera in coriander after that ekiga saw it. You do need to play around in coriander to get the best picture.

---

