---
title: "ASUS K40IN Ubuntu 12.04 NVIDIA Graphics Driver: 6 desktops!"
date: 2012-04-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kouyao on 2012-04-28
I deployed an absolute new installation on my ASUS K40IN Notebook, with NVIDIA GeForce G102M graphics.
The first time I installed Ubuntu 12.04 64bit and actived G102M's driver from "additional drivers". When I reboot my PC [COLOR="Red"]it showed 6 desktops, with each has a 640 x 480 resolution[/COLOR]. (**Normal resolution is 1366 x 768**)
I then uninstalled this driver (sudo apt-get --purge remove nvidia-*, then restart) and downloaded official GeForce G102M driver from wwww.nvidia.com (released on Apr 11, 2012, Linux 64 bit) but the same result.
I then reinstalled the 32bit Ubuntu 12.04 release. This time I tried both drivers from "additional driver" and official NVIDIA releases. Still, 6 desktops!
ASUS K40IN works well with the built-in driver with poor graphics performance. I disabled the built-in driver and attempted to try the official NVIDIA driver but it should work like this!
/etc/modprobe.d/disable--nouveau.conf:
```
blacklist nouveau
options nouveau modeset=0
```
Run the following instructions from one console:
```
sudo service lightdm stop
sudo sh ~/Download/NVIDIA-Linux-x86_64-295.40.run
// install NVIDIA official driver...
// sudo service lightdm start
// 6 desktops! Oops!:mad:
```

---

### Post by jarik1112 on 2012-08-11
I have same problem with Ubuntu 11.10 and 12.04. In all systems was installed latest nvidia driver (295 and ~302). When I install to my notebook Ubuntu 11.10 with v280 nvidia driver, it work corect. So I concluded that is the problem of nvidia.

---

