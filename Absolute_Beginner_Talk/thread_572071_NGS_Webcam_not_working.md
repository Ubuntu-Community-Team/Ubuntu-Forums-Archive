---
title: "NGS Webcam not working"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by aspie on 2007-10-10
I'm pretty new to Ubuntu, so apologies if this is answered elsewhere. I have looked to no avail.

Anyway, I have an NGS Bullseye webcam, and I believe that this should work with spca5xx or gspca drivers. I have tried to follow posts here about installing these drivers, but I still cannot get it working.

Here is some output, I think that it shows the webcam as "Z-Star Microelectronics Corp."

$ lsusb
Bus 004 Device 005: ID 0ac8:305b Z-Star Microelectronics Corp.
Bus 004 Device 002: ID 05e3:0606 Genesys Logic, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 005: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

When I try to test it I get this error:
$ xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-lowlatency)
can't open /dev/video0: Input/output error
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Input/output error
v4l2: open /dev/video0: Input/output error
v4l: open /dev/video0: Input/output error
no video grabber device available

Where do I start to fix this?

---

### Post by aspie on 2007-11-09
Anybody?

Here is a snippet from dmesg:

```
[   31.484858] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 

```

Doesn't It look like it should be working form this?

---

### Post by philinux on 2007-11-09
Install kopete from synaptic, run it then go to configure. Select devices. You webcam should appear. Kopete does a really good job.

---

### Post by nikolas68 on 2007-11-09
.....i have Skype installed....but i thought the camera was not going to work so i didn't bother to check....and besides there're some serious issues with the microphone: very very low volume.

---

### Post by aspie on 2007-11-09
> **philinux said:**
> Install kopete from synaptic, run it then go to configure. Select devices. You webcam should appear. Kopete does a really good job.

Hi,

Thanks for the suggestion.  I have now installed kopete, but when I try and configure the video device there is nothing to select in the drop down.

---

### Post by philinux on 2007-11-09
Is it a externally connected usb cam?

---

### Post by philinux on 2007-11-09
Looks like you need the gspca driver 

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

---

### Post by aspie on 2007-11-09
I have now installed the gspca driver, and nothing!!.  So, I unplugged the USB cable from the hub, and plugged it direct into a prt on my PC...  It worked!!!

Why?  I have no idea.  but I'm pretty happy now.  Of course i would liek to know why this made a difference.

Thanks for all your help.
Neil

---

### Post by philinux on 2007-11-09
Great stuff but weird.

OT what do you think of kopete

---

### Post by sailor2001 on 2007-11-09
usb takes a lot of juice, the farther away from your card on the mother board the less likely is it to work.. Much the same as slave vs master on the ribbon cable. cable.

---

### Post by sailor2001 on 2007-11-09
Skype now has webcam availability for linux..........go to their website

---

### Post by aspie on 2007-11-09
> **philinux said:**
> Great stuff but weird.

OT what do you think of kopete

kopete seems pretty good so far.  I will test it "in anger" over the weekend.

---

### Post by aspie on 2007-11-09
> **sailor2001 said:**
> usb takes a lot of juice, the farther away from your card on the mother board the less likely is it to work.. Much the same as slave vs master on the ribbon cable. cable.

Sure, but the strange thing is that it's OK on the hub under XP.

---

### Post by tashmooclam on 2007-11-09
I suggest you test it at [www.tokbox.com](www.tokbox.com) 
This is web-based, it's inside the browser. I think that means Flash actually runs it.
If your computer can "see" your webcam, this should work.
Using tokbox the person at the other end can use it also, nobody needs to be both running any chat program. They only need to have a browser running.

---

