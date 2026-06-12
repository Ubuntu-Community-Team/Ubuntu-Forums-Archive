---
title: "Wireless not working on MacBook Pro"
date: 2010-02-14
forum: Apple Hardware Users
---

### Post by uditramawat9 on 2010-02-14
I have a macbook pro. Model 5,3. I installed Ubuntu 9.10 today. After updating the drivers for everything, I still can not figure out the wireless Broadcom driver. The ethernet works out of the box. I even tried to select and active the Broadcom STA driver, but it does not get updated. And when I log in using an old Kernel version, it shows that the driver is active, but it still does not search and connect for wireless networks.
Please help.

P.S. I am triple booting - MAC OSX (snow leopard), Windows 7, Ubuntu 9.10

---

### Post by linuxopjemac on 2010-02-14
I read this in another forum thread:
> 
Wireless (AirPort)
To enable wireless you need to install the restricted Broadcom STA driver. If you don't have wired internet access, download these packages using another computer:

[http://packages.ubuntu.com/karmic/patch](http://packages.ubuntu.com/karmic/patch)
[http://packages.ubuntu.com/karmic/dkms](http://packages.ubuntu.com/karmic/dkms)
[http://packages.ubuntu.com/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/karmic/bcmwl-kernel-source)
Install them in this order (by pasting the URL in your browser) and downloading the package appropriate for your build, you can instal with a package manager. Then restart the computer.


Taken from the Debian Wiki.
I had the exact same problem and following these steps got my wireless working beautifully.
Also this is assuming your running Karmic.
see [http://ubuntuforums.org/showthread.php?t=961545&highlight=broadcom&page=2](http://ubuntuforums.org/showthread.php?t=961545&highlight=broadcom&page=2)

you could also face the bug, in that case uninstalling linux-backports-modules should fix that ([http://ubuntuforums.org/showthread.php?t=1401290&highlight=broadcom&page=2](http://ubuntuforums.org/showthread.php?t=1401290&highlight=broadcom&page=2))
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630)

Please report us what helped...

---

