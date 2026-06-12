---
title: "How do I unstall a tv card?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2008-03-29
Hi I installed a nova t-500 but it clashes with other hardware I use, so I'm changing my stem setup but how do I uninstall this device from ubuntu??

---

### Post by tony.morse on 2008-03-29
Ok so this is what I did to install the card...

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
wget [http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw)
sudo cp dvb-usb-dib0700-1.10.fw /lib/firmware
sudo apt-get install linux-headers-$(uname -r) build-essential 
sudo apt-get install mercurial
sudo apt-get install linux-source
cd /usr/src/
sudo tar -xjvf linux-source-2.6.22.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.22 /lib/modules/$(uname -r)/source
cd ~/
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
sudo apt-get install ncurses-dev
sudo make menuconfig
make
sudo make install
sudo make load
sudo modprobe dvb-usb-dib0700

The result is a working card but no more webcam (as the Nova-t-500 is a usb card I guess there is a conflict)  Anyway please please someone help a newbee out and tell me how to undo this.

Cheers

---

