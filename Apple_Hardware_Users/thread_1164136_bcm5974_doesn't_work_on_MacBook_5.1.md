---
title: "bcm5974 doesn't work on MacBook 5.1"
date: 2009-05-19
forum: Apple Hardware Users
---

### Post by larslarsson on 2009-05-19
Hi,

I have Intrepid on my MacBook 5.1 and most of the Mactel stuff works, but not bcm5974. I installed it from the dkms, and I did the fdi file thing and the usbhid blacklist (according to the threads here). bcm diagnostics says /proc/bus/input/devices: module NOT registered.

I'm running Ubuntu off of a USB stick, could it be that usbhid blacklist fails because of that?

I attach my /proc/bus/input/devices (added .txt). Can't find 'bcm' in it, should I? (If so, should I enter it manually?)

Thanks for any help!
Lars

---

### Post by cyberdork33 on 2009-05-19
is the module loaded?? (use 'lsmod')

---

### Post by larslarsson on 2009-05-19
lsmod says:
.....
bcm5974                17032  0 
....

So I guess it's loaded.

---

### Post by cyberdork33 on 2009-05-19
well, there is a bug open for this.
[https://bugs.edge.launchpad.net/mactel-support/+bug/337935](https://bugs.edge.launchpad.net/mactel-support/+bug/337935)

---

### Post by larslarsson on 2009-05-20
Thanks for the reply, but I have done the things described in that bug.
The only sure thing I know is that my  /proc/bus/input/devices does not contain bcm5974. 
Should/could it be added manually? 
And may this have to do with my using USB (running off of a USB stick)? If I connect a USB mouse, it works fine.....

---

### Post by cyberdork33 on 2009-05-20
> **larslarsson said:**
> Thanks for the reply, but I have done the things described in that bug.
The only sure thing I know is that my  /proc/bus/input/devices does not contain bcm5974. 
Should/could it be added manually? 
And may this have to do with my using USB (running off of a USB stick)? If I connect a USB mouse, it works fine.....
I really don't know, but you should post any relavant information to the bug report.

---

### Post by alexmurray on 2009-05-21
Did you make sure you [updated your initramfs]("http://bugs.edge.launchpad.net/mactel-support/+bug/337935/comments/50") after blacklisting usbhid?

---

### Post by larslarsson on 2009-05-22
Good point, but I did do the update-initramfs.
(Including substituting the update-initramfs from the Live CD with the one from rofs.)

Does anyone know if the /proc/bus/input/devices file should have bcm5974 in it?
And if it should, in what part of install or boot should it be inserted?

Thanks,
Lars

---

### Post by larslarsson on 2009-05-27
The problem was obviously usbhid blocking bcm5974, I tried: 
     rmmod bcm5974; rmmod usbhid; modprobe bcm5974; modprobe usbhid
and then it worked. Just need to find out how to make it persistent.

Lars

---

### Post by alexmurray on 2009-05-27
Make sure you follow the instuctions on the Wiki for blacklisting usbhid and it should all work and be persistent - I'd guess you've probably just missed a step somewhere...

---

