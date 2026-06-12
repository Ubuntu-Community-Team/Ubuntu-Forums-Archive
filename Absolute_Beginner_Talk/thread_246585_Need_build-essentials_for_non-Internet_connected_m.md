---
title: "Need build-essentials for non-Internet connected machine"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by BarkingSpider on 2006-08-29
I have installed xubuntu 6.06 on an old Gateway machine, but it does not recognize the network adapter card (D-Link DFE-530TX+). I cannot compile the driver from the CD-ROM, and was told I need to add build-essentials to my machine. 

All the other machines I have access to run Windows, so...

Can I run xubuntu from a Live CD on a Windows machine, add the build-essentials package, then manually add the package to my non-Internet connected machine?

Thanks!

---

### Post by kaamos on 2006-08-29
Yea, that should work. The files that you need are .deb files located in /var/cache/apt/archives after you have installed build essential. Copy them to a usb-drive or whatever and install in the Gateway with
```
sudo dpkg -i /path/to/files/*.deb
```

---

### Post by BarkingSpider on 2006-08-29
Thanks, kaamos.

I will try out this idea and post the results in a couple days.

---

### Post by aysiu on 2006-08-29
The *build-essential* package is actually on the CD itself: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by BarkingSpider on 2006-09-06
Thanks for the tip aysiu, I successfully added the build-essential package from the CD using your suggested commands. Now, I receive an error when I run the "Make Install" command. Where should I post my question about this new problem?

---

### Post by taurus on 2006-09-06
Shouldn't it be either "sudo make install" or "sudo checkinstall"!!!  You need to be root to install something on your system besides your $HOME.

---

### Post by az on 2006-09-06
> **BarkingSpider said:**
> Thanks for the tip aysiu, I successfully added the build-essential package from the CD using your suggested commands. Now, I receive an error when I run the "Make Install" command. Where should I post my question about this new problem?

Have you installed the linux-headers?

You need that for kernel modules.

Do not use checkinstall for kernel modules.

---

### Post by BarkingSpider on 2006-09-07
No problem about being root; I used "sudo" before the commands.

I have not installed the linux headers. I'm assuming they are on the CD too, and I can use apt-get (see I'm learning a little) for them. Would someone kindly include the commands?

---

### Post by BarkingSpider on 2006-09-07
The actual message when I try to compile the driver file using make install is

```
Makefile:16 *** Linux kernel source not found. Stop.
```

The driver files for the D-Link DFE-530TX+ adapter are located in the /temp/dlkfet-4.39 directory that I created.

I'm not sure how to check if the header files are installed. Any ideas?

---

