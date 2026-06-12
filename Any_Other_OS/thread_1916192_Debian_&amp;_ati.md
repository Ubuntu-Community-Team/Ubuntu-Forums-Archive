---
title: "Debian &amp; ati"
date: 2012-01-27
forum: Any Other OS
---

### Post by sunfromhere on 2012-01-27
The new ATI driver is out. In Ubuntu 11.10 I did this:
remove - purge fglrx
reboot
run the installer
And that was it.

I know Debian isn't Ubuntu, but they're similar enough. So I tried
remove - purge fglrx
And system crashes.

I ran recovery mode, reinstalled fglrx from repos but it's not the newest driver.

I also tried installing the newest driver from recovery mode, it gave this error:
[Error]A previous installation of fglrx driver detected to be loaded.
User must uninstall existing fglrx driver 
or run install with force option. 
Forcing the installation is not recommended.

(this is after remove&crash). Weird.
Any suggestions what to do here?

---

### Post by sunfromhere on 2012-01-28
I solved Debian: started in recovery mode, purged fglrx, located and deleted by hand every appearance of fglrx, deleted xorg.conf, reinstalled video-drivers-ati, mesa, xserver-xorg-core, and then did dpkg-reconfigure xserver-xorg. The installer ran at that point and successfully installed newest ati drivers.

But now the same issue happened with openSUSE. I never had proprietary drivers there, and the installation killed GUI.

So far, ati installation has gone flawlessly only in Ubuntu. The quality of ati drivers for Linux is another story...

---

### Post by Helen McCall on 2012-03-19
> **sunfromhere said:**
> I solved Debian: started in recovery mode, purged fglrx, located and deleted by hand every appearance of fglrx, deleted xorg.conf, reinstalled video-drivers-ati, mesa, xserver-xorg-core, and then did dpkg-reconfigure xserver-xorg. The installer ran at that point and successfully installed newest ati drivers.

So far, ati installation has gone flawlessly only in Ubuntu. The quality of ati drivers for Linux is another story...

I tend to agree with you on ATI drivers. The most annoying thing with them is that if your graphics card model number is not on the ATI driver list, but the functions are all supported in the driver, it still puts an annoying watermark in the bottom right of your screen which I have sofar found no way of removing!

---

