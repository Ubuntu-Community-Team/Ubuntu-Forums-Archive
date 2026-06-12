---
title: "How to install wifi drivers for Ubuntu on single-boot macbook"
date: 2018-10-04
forum: Apple Hardware Users
---

### Post by davidfrancaisf on 2018-10-04
I came into the possession of a MacBook Pro (Retina, 15-inch, Late 2013) with a clean hard drive, no OS or anything. I decided to install Ubuntu on it, and after a successful installation now have the issue that (I assume) it lacks the drivers to use the laptop's built-in wifi adapter, and it says that no adapter is found. Worth mentioning again that this is a single boot laptop, Ubuntu is the only OS on it at the moment. Any help is appreciated.

---

### Post by gsahli on 2018-10-04
I don't have a Macbook Pro, but I know it has a broadcom B43xx wifi chip. You need to install the firmware for that chip from the repositories OR from your original install media.
Try following this:
[https://askubuntu.com/questions/730799/installing-firmware-b43-installer-offline](https://askubuntu.com/questions/730799/installing-firmware-b43-installer-offline)

---

### Post by MikeBraxner on 2018-10-06
Have a look at this [post]("https://ubuntuforums.org/showthread.php?t=2305509&p=13404018#post13404018"), it should have you sorted out in short order.

---

### Post by davidfrancaisf on 2018-10-06
> **MikeBraxner said:**
> Have a look at this [post]("https://ubuntuforums.org/showthread.php?t=2305509&p=13404018#post13404018"), it should have you sorted out in short order.
So this hasn't fixed the problem, but it's revealed a new one. For some reason, many, or even all of the debian packages in the boot disk were not installed at all, and attempting to install them manually doesn't work. I press install, it asks for a password, and then nothing appears to change, the install button is still there.
What I then tried doing is installing them through the terminal, and this revealed that the two .deb packages I needed to install have many dependencies that were not installed during the installation of ubuntu. It should be said that I've tried reinstalling ubuntu (with a new download as well) and the problem persists.

I'm not sure if I should make a new thread at this point.

---

### Post by gsahli on 2018-10-06
Is this Ubuntu 18.04? Installed from USB flash drive? flash drive made how? Installed using EFI mode?
Does this help?
[http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/)

---

### Post by davidfrancaisf on 2018-10-06
> **gsahli said:**
> Is this Ubuntu 18.04? Installed from USB flash drive? flash drive made how?

Yeah it's 18.04. I installed from a flash drive made using Ubuntu Startup Disk Creator.

---

### Post by gsahli on 2018-10-06
Sorry - I made changes above.

PS- the Ubuntu 18.04 package for B43xx is "firmware-b43-installer."

---

### Post by MikeBraxner on 2018-10-06
Just a thought ... did you connect to the internet during installation, and allow the install process to download upgrades while installing? If so, then the needed dependencies are on the usb drive, but unfortunately out of date, since you downloaded updated version during install, for which the dependencies arn't available. 

While there are ways around this, I would suggest the simpler route of a fresh install, **without** internet connection, and then try again the previously mentioned post.

---

### Post by oa+ on 2018-10-06
Thanks for sharing this.. i just gain a knowledge here..

---

### Post by gsahli on 2018-10-06
You don't need to do any of the stuff regarding the kernel. Just "firmware-b43-installer."
Read here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

```
 Installing b43/b43legacy firmware
The Ubuntu kernel now provides the b43 driver, however due to copyright restrictions not the proprietary firmware which is required to run your card. 
```

---

