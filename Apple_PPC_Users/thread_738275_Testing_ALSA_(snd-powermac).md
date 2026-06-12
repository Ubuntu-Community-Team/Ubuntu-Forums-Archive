---
title: "Testing ALSA (snd-powermac)"
date: 2008-03-28
forum: Apple PPC Users
---

### Post by ristosu on 2008-03-28
I've been trying to fix ALSA support for older PowerMacs. Anyone experiencing problems - like missing or inoperative or wrongly directed controls in alsamixer - could you, please, test my patches and write the results into this thread or directly to me?

If you are still with me, check first with lsmod that you are using snd-powermac:
```
risto@orange:~$ lsmod | grep ^snd.powermac
snd_powermac           56576  0 
risto@orange:~$
```
Then you will need to install make, C-compiler and kernel headers corresponding to your running kernel, f.ex (Dapper 6.06.1):
```
sudo aptitude install make gcc linux-headers-2.6.15-26-powerpc
```
and fetch the ALSA driver source code and my patch:
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2
wget http://ristosu.wippiespace.com/pub/alsa-driver-1.0.16-p4.diff
```
Unpack the source and apply the patch:
```
tar xjf alsa-driver-1.0.16.tar.bz2
cd alsa-driver-1.0.16
patch -p0 < ../alsa-driver-1.0.16-p4.diff
```
Finally configure:
```
./configure --disable-verbose-printk --with-kernel=/usr/src/linux-headers-2.6.15-26-powerpc --with-build=/usr/src/linux-headers-2.6.15-26-powerpc --with-moddir=/lib/modules/2.6.15-26-powerpc/updates/sound --with-isapnp=no --with-oss=yes --with-pcm-oss-plugins=yes --with-cards=powermac
```
make and install:
```
make
sudo make install-modules
```
To load the new modules without rebooting:
```
sudo modprobe -r snd-powermac
sudo modprobe -r snd-pcm-oss
sudo modprobe snd-powermac
```

---

### Post by ubuntubrian on 2008-03-28
What version of Ubuntu are you working with? Is this an effort to get sound working?
Curious!

---

### Post by ristosu on 2008-03-28
Yes, it is. I've done my testing on Dapper, and I believe it should work at least on newer releases, too.

---

### Post by rwhitehair on 2008-03-28
would this work on an Ibook g4?

---

### Post by ristosu on 2008-03-29
Yes, it should, but I have not done any changes in that part of the driver. Only older Macs with Screamer or Burgundy sound codecs are concerned.

---

