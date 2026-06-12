---
title: "Ubuntu 11.04 and 10.04 on iLamp iMac freezes on boot"
date: 2011-04-28
forum: Apple Hardware Users
---

### Post by fabioscky on 2011-04-28
Hi,
I tried to boot live Ubuntu (using 11.04 daily build) and 10.04 on my G4 iMac (the so-called iLamp) 15" but it freezed on boot.
I tried using both the "live" and the "live video=ofony" options with no difference.
The result is always a white or blank screen (randomly). With 10.04 I obtained a little bit different result: a yellow screen!
These are the main characteristics of my iMac (obtained with the system profiler):
PowerMac 4.2
CPU PPC G4 700MHz
576MB Ram

Video:
NVIDIA GeForce2 MX
ROM Revision: 1057.008.1

Does anyone know of a workaround to solve this problem?
I am a beginner with Ubuntu (I just used it a little on my Eee PC 900).
Thanks.
Fabio.

---

### Post by linuxopjemac on 2011-04-28
I guess you need a working xorg.conf as a start. 

I would start with the nv driver in there. In a terminal:
```
wget [http://mac.linux.be/files/xorg/imac8.txt](http://mac.linux.be/files/xorg/imac8.txt)
sudo mv imac8.txt /etc/X11/xorg.conf
sudo echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
sudo update-initramfs -u

```
reboot

If you want to experiment more with nouveau, tell me.

---

### Post by fabioscky on 2011-04-28
Thanks for your replay, but (sorry I forgot to write it in my post) I was trying to boot from the live CD (I didn't try to install it yet).
From your answer I suppose you told me to modify my installation (by the way I also don't know how to enter the teminal window during the boot process) and I will consider it if I decide to install it.
Thanks again.
Fabio.

---

### Post by linuxopjemac on 2011-04-29
Go for the alternate installer (no GUI):
[http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso)
[http://cdimage.ubuntu.com/ports/releases/maverick/release/ubuntu-10.10-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/maverick/release/ubuntu-10.10-alternate-powerpc.iso)

---

### Post by fabioscky on 2011-04-30
Thanks linuxopjemac,
I will get in a few days another hard disk (since I don't want to delete the original OSX and my hard disk is almost full), with this I will try your suggestion.
Bye.
Fabio.

---

