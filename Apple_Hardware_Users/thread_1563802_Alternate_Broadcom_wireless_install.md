---
title: "Alternate Broadcom wireless install?"
date: 2010-08-29
forum: Apple Hardware Users
---

### Post by vdubeau on 2010-08-29
If I boot Ubuntu from the live disc, the Broadcom installs and activates flawlessly. I installed Ubuntu (Lucid) to my hard drive and it seems to be reading the CD but then gets and error saying it couldn't find the driver.

I only have wireless available to me so ethernet is not an option. Is there another way to download the needed the packages in OS X and then install them in Ubuntu?

---

### Post by linuxopjemac on 2010-08-30
> 2. IF WIRED CONNECTION DOES NOT WORK:
1. From LiveCD (solution provided by jomtois here - edited for clarity):
1. Open Sytem -> Admin -> Synaptic Package Mgr
2. Ensure 9.10 LiveCD is in the drive
3. In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
4. Check "Installable from CD-ROM/DVD" and close
5. Reload (disregard connectivity errors)
6. Search for "bcmwl-kernel-source"
7. Right-click and mark for installation
8. Apply changes and reboot
9. After reboot, open System -> Admin -> Hardware Drivers
10. Look for "Broadcom STA wireless driver";

This was the [guide]("http://ubuntuforums.org/showthread.php?t=1368699") for Karmic Koala, I guess it still applies...

---

### Post by halj32 on 2010-08-30
try installing dkms, fakeroot, patch, and then the bcmwl-kernel-source package from the live-cd
works for me on a Dell inspiron

---

### Post by vdubeau on 2010-08-31
Thanks halj32. That worked perfectly.

---

### Post by notabs on 2010-09-01
Hi Halj32,

I am experiencing similar issue. When boot from CD, install of bcmwl-kernel-source works flawlessly from menu - system|administration|hardware drivers.  If I then install on USB drive and boot from USB, it does not work - from the CD as mentioned above, or from the system|administration|hardware drivers menu choice.

I want to try your method, when booting from USB, but am linux newbie (please forgive my newbieness). can you type in the commands as I would use them in terminal to accomplish the steps you outlined below to install dkms, fakeroot, patch?

FYI, I am running 64bit ubuntu 10.04.1 on dell latitude E6510 with dw1520 mini wireless N halfcard if it matters.


> **halj32 said:**
> try installing dkms, fakeroot, patch, and then the bcmwl-kernel-source package from the live-cd
works for me on a Dell inspiron


thanks

NOTABS
(not a brain surgeon)

---

### Post by hipstersandwich on 2010-09-02
Thanks much, I had problem with my wifi and this fixed it.  I am now writing my first post in Ubuntu and no longer have to use my OSX partition to get online.

---

