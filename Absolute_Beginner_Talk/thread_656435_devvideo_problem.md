---
title: "/dev/video problem"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2008-01-02
Hi, when I try to install my DVB card I loose my webcam, so what I do is...

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

 * Very Important Turn on the onboard amplifier or you will get very poor signal strength.
sudo gedit /etc/modprobe.d/options
Add: options dvb-usb-dib0700 force_lna_activation=1 

sudo make load
sudo modprobe dvb-usb-dib0700

Now I've already reinstalled my system from scratch to get my webcam back, but this install looses /dev/video0 completely.  If I remove the line added to options, and do it all again, then I get a /dev/video0 but it's no longer my webcam but a picture of coloured stripes, presumably from my tv card?  

Anyway how do I get my webcam back?
Why does this change /dev/video0?
What should I do about it?

All help really apreciated

---

### Post by fiddledd on 2008-01-03
This probably won't help, but all I did to get my DVB usb2(I know yours is a card) working was copy the firmware to /lib/firmware and everything works fine using kaffeine.

---

