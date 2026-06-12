---
title: "webcam issues"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by benfindlay on 2007-11-27
Hi guys. Ive been trying to get my webcam to work for a while now but with no luck. Im using a program called motion which detects movement via a webcam. The camera is a PC Line Webcam 300k

The camera is recognised by the system as shown here from the output of lsusb:

> Bus 005 Device 005: ID 04fc:0c15 Sunplus Technology Co., Ltd
Bus 005 Device 003: ID 1058:0910 Western Digital Technologies, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
**Bus 004 Device 004: ID 093a:2600 Pixart Imaging, Inc.**
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 004: ID 05ac:0306 Apple Computer, Inc.
Bus 003 Device 003: ID 05ac:0205 Apple Computer, Inc. Apple Extended Keyboard [Mitsumi]
Bus 003 Device 002: ID 05ac:1002 Apple Computer, Inc. Apple Extended Keyboard Hub [Mitsumi]
Bus 003 Device 001: ID 0000:0000


However, when I try and start motion it says
> Failed to open video device /dev/video0: No such file or directory


Anyone have any ideas?

---

### Post by meborc on 2007-11-27
the webcam might be in /dev/video1 ... so you could try editing the motion conf file... more info on motion here [http://www.lavrsen.dk/twiki/bin/view/Motion/MotionGuideGettingItRunning](http://www.lavrsen.dk/twiki/bin/view/Motion/MotionGuideGettingItRunning)

the device motion will use is video0 by default

---

### Post by benfindlay on 2007-11-27
Hey, thanks for the quick reply!

Just tried that and no joy. Looking through the contents of my /dev/ directory reveals no entried titled video0 or video 1 (or video anything for that matter).

Am I able to add an entry at all?

---

### Post by meborc on 2007-11-27
> **benfindlay said:**
> Hey, thanks for the quick reply!

Just tried that and no joy. Looking through the contents of my /dev/ directory reveals no entried titled video0 or video 1 (or video anything for that matter).

Am I able to add an entry at all?

doing it by hand (adding a directory) would not help... i guess you should try to find drivers for that spesific webcam

EDIT: ok, it seems you need these drivers gspcav1 as listed on this site [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

EDIT2: [http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz)  this is the driver you most probably need... as far as i understand

---

