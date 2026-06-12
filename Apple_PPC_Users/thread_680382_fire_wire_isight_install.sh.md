---
title: "fire wire isight_install.sh"
date: 2008-01-27
forum: Apple PPC Users
---

### Post by slink44 on 2008-01-27
hello,

has any body got the firewire isight  (i believe this is the original isight) working on the g5 powerpc tower. (1.6ghz i think this was the original g5 machine)?

i tried some of the other solutions to get this working.

sudo modprobe -r uvcvideo
sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.original
sudo apt-get update
sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r)
wget [http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz](http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz)
tar -xzvf uvcvideo-isight.tar.gz
cd against-revision-140
sudo make
sudo make install
sudo modprobe uvcvideo

---

### Post by oswaldkelso on 2008-01-29
> **slink44 said:**
> hello,

has any body got the firewire isight  (i believe this is the original isight) working on the g5 powerpc tower. (1.6ghz i think this was the original g5 machine)?

i tried some of the other solutions to get this working.

sudo modprobe -r uvcvideo
sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.original
sudo apt-get update
sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r)
wget [http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz](http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz)
tar -xzvf uvcvideo-isight.tar.gz
cd against-revision-140
sudo make
sudo make install
sudo modprobe uvcvideo

Mine works ok on debian with ekiga i'll look for my notes G4 ppc.

[http://ubuntuforums.org/showthread.php?t=251381](http://ubuntuforums.org/showthread.php?t=251381)

---

