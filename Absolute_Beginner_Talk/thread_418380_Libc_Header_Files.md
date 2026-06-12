---
title: "Libc Header Files????????????"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Urko on 2007-04-22
Hello to everyone:)

I am using Ubuntu 7.04 vith NVIDIA MX 440 graphic card. Latest Nvidia graphic drivers do not support my graphic card so I tried to install older one. First I download NVIDIA-Linux-x86-1.0-9631-pkg1.run drivers. Than I do next step:

CTRL+ALT+F1
$ sudo /etc/init.d/gdm stop
$ chmod a+x NVIDIA-Linux-x86-1.0-9631-pkg1.run
$ sudo ./ NVIDIA-Linux-x86-1.0-9631-pkg1.run

When Nvidia screen shows an give me some questions if I want to configure exsisting Kernel to match to this drivers give me following error :

YOU DON'T APPEAR TO HAVE LIBC HEADER FILES INSTALLED ON YOUR COMPUTER. YOU MUST INSTALL DISTRIBUTION LIBC DEVELOPMENT PACKAGE FIRST!!!!

Becouse I am new in Linux I don't know what  LIBC HEADER FILES are and how to install them?????

Enybody know what can I do next?????

Thenx Urko:confused:

---

### Post by Bachstelze on 2007-04-22
```
sudo apt-get install build-essential xorg-dev pkg-config linux-headers-$(uname -r)
```

No need to backup your xorg.conf, the installer will do it for you.

---

### Post by Swab on 2007-04-22
Try:
sudo apt-get install libc6-dev


I have the same card, and was not able to get it working with the driver in the repos or with the driver from the nvidia site.  

Anyway, back up your xorg.conf file before proceeding so you can restore it if X fails to start.

---

