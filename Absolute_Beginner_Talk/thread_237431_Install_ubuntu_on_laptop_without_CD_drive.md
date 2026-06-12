---
title: "Install ubuntu on laptop without CD drive"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by mcdermott_c on 2006-08-16
Hi

New to linux although i have installed it before and played around with it. I was wondering how I could install ubuntu on a sony srx41p which doesnt have a built in CD drive. I dont have an external cd drive either however I wondered if it was possible to install without a CD drive (i do have a USB external hard disk) and if there were any good step by step guides on how to do this.

Many thanks for the help

Chris

---

### Post by mcneely.mike on 2006-08-16
> **mcdermott_c said:**
> Hi

New to linux although i have installed it before and played around with it. I was wondering how I could install ubuntu on a sony srx41p which doesnt have a built in CD drive. I dont have an external cd drive either however I wondered if it was possible to install without a CD drive (i do have a USB external hard disk) and if there were any good step by step guides on how to do this.

Many thanks for the help

Chris

Hmmm... i would say that the easiest way to do it would be to take the external hard disk to a friends house who has a computer with a cd drive and plug it in to their computer. then install to the external hard disk (not your friends hard disk).  then bring it home and plug it back into your computer.

never tried it, but i think it should boot as long as grub points to the external hard disk.

hope it helps[-o<

---

### Post by seshomaru samma on 2006-08-16
well , [this ]("http://www.bigmaninjapan.com/2005/10/16/install-ubuntu-510-breezy-from-a-flash-disk/") explains how to install Breezy (an older version) from a USB flash disk. Installing Dapper (the current version) should be similar ,except instead of downloading the Breezy netinstall iso , you will have to download the Dapper netinstall iso. which you can find[ here ]("http://lists.linux.sk/pipermail/ubuntu-users/2006-July/000003.html") (the bottom of the page)
also in the commands they give, replace any 'Breezy' with 'Dapper'

good luck

---

### Post by seshomaru samma on 2006-08-16
> **mcneely.mike said:**
> Hmmm... i would say that the easiest way to do it would be to take the external hard disk to a friends house who has a computer with a cd drive and plug it in to their computer. then install to the external hard disk (not your friends hard disk).  then bring it home and plug it back into your computer.

never tried it, but i think it should boot as long as grub points to the external hard disk.

hope it helps[-o<

this would work , if your friend has the exact same hardware setting as you..

---

### Post by lupine_nickt on 2006-08-16
Since the default kernel includes a vast array of drivers, and the only thing the installer does differently between installations is the network settings, it should work fine...


...with the caveat that the OP would need to tweak the boot process on his/her system manually.

xF,

...Nick

---

### Post by seshomaru samma on 2006-08-16
> **lupine_nickt said:**
> Since the default kernel includes a vast array of drivers, and the only thing the installer does differently between installations is the network settings, it should work fine...


...with the caveat that the OP would need to tweak the boot process on his/her system manually.

xF,

...Nick

You are probably right , I work with really old hardware so I'm always careful....

---

### Post by Frank Golden on 2006-08-16
> **seshomaru samma said:**
> You are probably right , I work with really old hardware so I'm always careful....
Can your laptop boot from a USB flash drive? If it can read this.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUsb%29](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUsb%29)

I walks you through setting up on a USB flash drive. You need the Ubuntu DesktopCD iso and a way to mount and read iso. Nero7works for me. I am
a relative Ubuntu newbie (less than year) and was able to install the Desktop CD on a 2 GB mini Cruzer. It works great.

---

