---
title: "Mounting a Olympus W-10 digital voice recorder"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by pathum on 2007-05-21
i have a Olympus W-10 Digital Voice Recorder which I was able to connect to my Windows system using the software provided for the device. Now I've turned to Linux and can't seem to find a way to access the files inside the recorder which is connected via USB. I tried searching for Linux drivers but failed. Apperantly there is no Linux version of the software or the driver? Can someone pls help? 
Thanks.

---

### Post by hryanjones on 2008-02-26
I have the same problem (Olympus Digital Voice Recorder - VN-3100PC) not recognized.

The only thing I found was that an 'ls -l /dev/u*' looked like this before plugging it in:

crw-rw-rw- 1 root root   1, 9 2008-02-26 10:46 /dev/urandom
crw-rw---- 1 root root 254, 0 2008-02-26 10:46 /dev/usbdev1.1_ep00
crw-rw---- 1 root root 254, 1 2008-02-26 10:46 /dev/usbdev1.1_ep81
crw-rw---- 1 root root 254, 2 2008-02-26 10:46 /dev/usbdev2.1_ep00
crw-rw---- 1 root root 254, 3 2008-02-26 10:46 /dev/usbdev2.1_ep81


And like this after:

crw-rw-rw- 1 root root   1, 9 2008-02-26 10:46 /dev/urandom
crw-rw---- 1 root root 254, 0 2008-02-26 10:46 /dev/usbdev1.1_ep00
crw-rw---- 1 root root 254, 1 2008-02-26 10:46 /dev/usbdev1.1_ep81
crw-rw---- 1 root root 254, 4 2008-02-26 11:09 /dev/usbdev1.2_ep00
crw-rw---- 1 root root 254, 6 2008-02-26 11:09 /dev/usbdev1.2_ep02
crw-rw---- 1 root root 254, 5 2008-02-26 11:09 /dev/usbdev1.2_ep81
crw-rw---- 1 root root 254, 7 2008-02-26 11:09 /dev/usbdev1.2_ep83
crw-rw---- 1 root root 254, 2 2008-02-26 10:46 /dev/usbdev2.1_ep00
crw-rw---- 1 root root 254, 3 2008-02-26 10:46 /dev/usbdev2.1_ep81

That was the only change I found, but which to mount and what filesystem type.  Too much of a newb to know.  Help us!

---

