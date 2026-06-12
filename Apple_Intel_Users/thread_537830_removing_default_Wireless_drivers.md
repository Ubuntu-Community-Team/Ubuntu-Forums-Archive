---
title: "removing default Wireless drivers"
date: 2007-08-29
forum: Apple Intel Users
---

### Post by trevelyn on 2007-08-29
hi,  i got this weird question.. i am using Feisty Fawn Ubuntu on my MacBook, and when i install it, it comes with a gerneric ralink driver i think.  But, i need that to get out of the machine! :S  when i plug my WUSB54GC ralink card into my computer, it uses a worong driver, the driver i want to use is a serialmonkey driver.  uhh, it is listed in dmesg as a ralink card, but was given a prism nick "wlan0" i am very used to using "rausb0" and decided to just install the serialmonkey driver anyways, and yeah even after reboot the card was listed as "wlan0" and theres also a psuedo device listed as "eva0-wlan" or something.. 
is there anyway i can just get rid fo these drivers so i can use my own???
thanks in advance - trev.

---

### Post by cyberdork33 on 2007-08-29
> **trevelyn said:**
> hi,  i got this weird question.. i am using Feisty Fawn Ubuntu on my MacBook, and when i install it, it comes with a gerneric ralink driver i think.  But, i need that to get out of the machine! :S  when i plug my WUSB54GC ralink card into my computer, it uses a worong driver, the driver i want to use is a serialmonkey driver.  uhh, it is listed in dmesg as a ralink card, but was given a prism nick "wlan0" i am very used to using "rausb0" and decided to just install the serialmonkey driver anyways, and yeah even after reboot the card was listed as "wlan0" and theres also a psuedo device listed as "eva0-wlan" or something.. 
is there anyway i can just get rid fo these drivers so i can use my own???
thanks in advance - trev.

I am not exactly sure what all you are trying to do, but you can blacklist modules in /etc/modprobe.d/blacklist and that will prevent them from loading.

---

### Post by trevelyn on 2007-08-29
ok, i got it working this time when i installed(or reconfigured) the cards i did the usb card first, and THEN the built in card, and i made a tutorial for myself, so i can do it again if i ever need to.
> 
try this next time you reinstall ubuntu on the macbook:
1. go through the install process.
2. install the usb card first by doing this:

sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4
 ***- then download the drivers from here: [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) 
sudo cp /path/to/file/rt73-cvs-daily.tar.gz /usr/src/
cd /usr/src
sudo tar -xzvf rt73-cvs-daily.tar.gz 
cd rt<tab>/Module
sudo make
sudo make install
sudo mkdir /lib/modules/`uname -r`/drivers/
sudo cp /lib/modules/2.6.12/extra/rt73.ko /lib/modules/`uname -r`/drivers/
sudo insmod /lib/modules/`uname -r`/drivers/rt73.ko
sudo lsmod -a
modprobe rt73
***-optional sudo /etc/init.d/networking restart (i didnt do this, i rebooted after it was all over)
sudo echo rt2570 >> /etc/modules
reboot

3. install the madwifi Atheros Built-In card by doing this:
wget [http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2695-20070829.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2695-20070829.tar.gz)
tar vzxf madwifi-ng-r2695-20070829.tar.gz
cd madwifi-ng-r2695-20070829
make
make install
modprobe ath_pci

there should be now a wifi0 device and a pseudo ath0 device.
to put the card into monitor mode, do 
wlanconfig ath0 destroy
***pseudo ath0 will be gone from iwconfig and ifconfig, you just have to remake it:
airmon.sh start wifi0


Its just weird cos, the card is still named wrong, but this time after probing the kern module, the other card didnt fail, so .. i guess i can live with "wlan0" as long as it works :) thanks again.

---

