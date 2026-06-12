---
title: "FreeBSD 9.1 Packages not found"
date: 2013-03-17
forum: Any Other OS
---

### Post by createdcreature on 2013-03-17
Hi, I have just installed the 64 bit (amd64) version of FreeBSD 9.1 in a VM in VirtualBox. I am not a newbie to FreeBSD, Linux, or Unix in general. It's great, but I have one massive problem. When I try and install a package (e.g. pkg_add -r packagename), it cannot find the package. It DOES have internet connectivity (I have successfully pinged [www.google.com]("http://www.google.com")). I went to the site it is trying to get to in a web browser, and found that the folder it is trying to get to does not exist. Is there any way to change the folder that pkg_add gets the packages from on the FTP server, so that it gets them from the 9.0_release folder rather than the non-existent 9.1_release fi? Your help is greatly appreciated!

---

### Post by haqking on 2013-03-17
> **Robert Moyse said:**
> Hi, I have just installed the 64 bit (amd64) version of FreeBSD 9.1 in a VM in VirtualBox. I am not a newbie to FreeBSD, Linux, or Unix in general. It's great, but I have one massive problem. When I try and install a package (e.g. pkg_add -r packagename), it cannot find the package. It DOES have internet connectivity (I have successfully pinged [www.google.com]("http://www.google.com")). I went to the site it is trying to get to in a web browser, and found that the folder it is trying to get to does not exist. Is there any way to change the folder that pkg_add gets the packages from on the FTP server, so that it gets them from the 9.0_release folder rather than the non-existent 9.1_release fi? Your help is greatly appreciated!

[http://www.cyberciti.biz/tips/freebsd-changing-pkg_add-package-ftp-site-location.html](http://www.cyberciti.biz/tips/freebsd-changing-pkg_add-package-ftp-site-location.html)

[http://forums.freebsd.org/showthread.php?t=3504](http://forums.freebsd.org/showthread.php?t=3504)

---

### Post by createdcreature on 2013-03-18
Thanks, haqking!

---

