---
title: "Installing fglrx from usb drive in recovery"
date: 2007-10-30
forum: Apple Intel Users
---

### Post by schauerlich on 2007-10-30
I'm trying to install fglrx on a 17" iMac with ATI graphics. I can't get into gdm and I've reset xorg twice (ati and vesa) and it hasn't helped. I'm behind a firewall at school and can't download fglrx, so I have it on a flash drive. How do I install fglrx from the flash drive in recovery?

---

### Post by cyberdork33 on 2007-10-30
> **EDavidBurg said:**
> I'm trying to install fglrx on a 17" iMac with ATI graphics. I can't get into gdm and I've reset xorg twice (ati and vesa) and it hasn't helped. I'm behind a firewall at school and can't download fglrx, so I have it on a flash drive. How do I install fglrx from the flash drive in recovery?

There is more that one package that you need to install, and you need the packages that matches your current kernel.

[Unofficial ATI wiki instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way")
I would take this to mean that you need the 'linux-restricted-modules-generic' package and the 'xorg-driver-fglrx'. Why can you not update normally on whatever connection you are downloading the package on?

---

### Post by schauerlich on 2007-10-30
I downloaded the package from my home computer, and I need to install it on the one at school. When I try to download it from the school computer, I get a "could not resolve [URL]" error.

---

