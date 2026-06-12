---
title: "No Wireless on MacbookPro5.5"
date: 2009-11-06
forum: Apple Hardware Users
---

### Post by Cerin on 2009-11-06
I'm following the guide at [https://help.ubuntu.com/community/MacBookPro5-5/Jaunty](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty) for installing Ubuntu on a MacbookPro5.5. Everything seems to be going smoothly, with the exception of no wireless.

The author states this works out of the box, and that the "Broadcom STA wireless driver" is activated by default, but this is not the case for me. This driver is listed in the Hardware Drivers installer, but when I activate it, nothing happens. The progress dialog clears and no errors are reported, but the driver still isn't activated. How do I activate this wireless driver?

Regards,
Chris

---

### Post by Cerin on 2009-11-06
I tried following the guide at [http://forum.notebookreview.com/showthread.php?t=418403#wireless](http://forum.notebookreview.com/showthread.php?t=418403#wireless), and while the "Hardware Drivers" dialog now shows the "Broadcom STA wireless driver" is installed and activated, network manager doesn't seem to see and wireless interface.

Even worse, if I try to deactivate any driver, I get the error "SystemError: installArchives() failed".

---

### Post by Cerin on 2009-11-06
Fixed by following the instructions at [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8261801](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8261801)

---

### Post by z0rd on 2009-11-17
Same problem here. The solution posted before seems to be not working for me. Any suggestions?

---

### Post by z0rd on 2009-11-18
After several problems I managed installing the bcmwl-kernels-source. But now I'm stuck at:

```

root@foo:~# modprobe wl
FATAL: Could not read '/lib/modules/2.6.31-14-generic/updates/dkms/wl.ko': Invalid argument

```

---

### Post by Cerin on 2009-11-18
You'd be better off posting in the other thread I link to. Note, I didn't have any luck with wl. My wireless actually started working after I removed that module and just used the default bcm43xx module.

---

