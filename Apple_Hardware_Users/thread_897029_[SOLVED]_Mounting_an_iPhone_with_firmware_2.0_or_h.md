---
title: "[SOLVED] Mounting an iPhone with firmware 2.0 or higher under 'buntu"
date: 2008-08-21
forum: Apple Hardware Users
---

### Post by fululian on 2008-08-21
Hullo,

I couldn't find a solution to this rather simple question - how do I mount my iPhone with firmware 2.0 unter ubuntu? When put into the USB-plug, it will charge, it is reachable under SSH, and a window will pop up asking if I would like to import any fotos. But the iPhone will not show up under /media whatever. The "official" way on the canonical sites tells us that you cannot sync with firmware 2.0 or higher, but that you may mount the device. But it doesn't. If I punch in

```
iphone-mount
```

the terminal tells me

```
fululian@fmtowns:~$ iphone-mount
touch: can't touch „/media/iphone/test“: Permission denied
Unable to write to /media/iphone.  Please adjust permissions and try again.

```

-what do I do with this? How *can* I adjust the permissions?

Thanks a lot.

---

### Post by cyberdork33 on 2008-08-21
> **fululian said:**
> How *can* I adjust the permissions?
sudo

---

### Post by fululian on 2008-08-22
No. But thanks nevertheless.

---

### Post by fululian on 2008-08-22
In this case, a simple

```

sudo chmod 777 /media/iphone
```

did the trick - supposing you joined the group "fuse", which I never heard of up to this day.

Bye bye

---

### Post by jack frost on 2008-10-08
if you want to run virtual machine for xp in virtual box.. I foud this and it works for syncing with itunes in virtual box.
 
[I]I was able to get my iPhone to sync. My setup:

Ubuntu 8.04 (Hardy Heron)
[[COLOR=#444444]VirtualBox 2.0.2[/COLOR]]("http://download.virtualbox.org/virtualbox/2.0.2/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb")
iPhone 3G (Software version 2.1)

I followed the steps mentioned in the thread on the virtualbox website

[[COLOR=#444444]http://www.virtualbox.org/ticket/491#comment:52[/COLOR]]("http://www.virtualbox.org/ticket/491#comment:52")

In particular, I did this:

[FONT=Courier New]sudo apt-get build-dep linux-source-2.6.24
sudo apt-get install linux-source-2.6.24 build-essential
tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot[/FONT][/I]

---

### Post by fululian on 2008-10-09
We will check this out. Thank you.

---

