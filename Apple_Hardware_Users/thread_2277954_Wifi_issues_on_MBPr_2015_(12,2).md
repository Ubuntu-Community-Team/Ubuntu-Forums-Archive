---
title: "Wifi issues on MBPr 2015 (12,2)"
date: 2015-05-12
forum: Apple Hardware Users
---

### Post by sundragon2 on 2015-05-12
I've managed to install Ubuntu on an SDcard - boots, works, happy happy. Great tutorial on this [http://teslabs.com/articles/ubuntu-15-04-mbp-11-2/#comment-2020153043](http://teslabs.com/articles/ubuntu-15-04-mbp-11-2/#comment-2020153043)

I cannot get the wifi to work.

The Wifi chipset is a BCM4360. (I've also seen it corrected to BCM43602??)

I tried enabling the driver in Software & Updates > Additional Drivers. Ubuntu hangs 
I used terminal to install the following drivers offline:

$sudo dpkg -i bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_amd64.deb dkms_2.2.0.3-2ubuntu3_all.deb


[LIST]
[*]bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_amd64.deb
[*]dkms_2.2.0.3-2ubuntu3_all.deb
[/LIST]

This caused the system to freeze at ""DKMS": install complete""

I rebooted and tried reinstalling using Ubuntu Software Installer which caused it to hang.

I attached the Apple Thunderbolt to Ethernet adapter in an attempt to get access to the web and that wasn't recognized (nothing happened)

I'm a noob at linux so please bare with me.

I've not messed with anything else, can someone please explain what I am doing wrong?

---

### Post by rican-linux on 2015-05-12
Take a look at **[this]("https://askubuntu.com/questions/592555/installing-broadcom-wireless-drivers-for-chip-id-bcm4360-pci-id-14e443a0")**.

---

### Post by sundragon2 on 2015-05-12
Thanks but the two packages listed in that link are the same ones I'm using. Maybe I'm missing something.

---

