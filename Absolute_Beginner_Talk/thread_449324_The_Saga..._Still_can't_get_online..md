---
title: "The Saga... Still can't get online."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-05-20
The story so far:  [http://ubuntuforums.org/showthread.php?p=2687685#post2687685]("http://ubuntuforums.org/showthread.php?p=2687685#post2687685")

I know it's bad form to open another thread while another's still going on the same problem but, well, if it gets help... 

I can't get online with my wireless card.  I've *tried* installing 'rt2x00' with these instructions: 

Quote:
sudo apt-get install build-essential linux-headers-$(uname -r)
This will install necessary packages for the compilation, after typing your password.

and then:

Quote:
wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
tar -xzf rt2500-cvs-daily.tar.gz
cd ./rt2500*/Module
make
sudo ifdown ra0
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2x00-legacy/rt2500/
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/ubuntu/wireless/rt2x00-legacy/rt2500
echo "alias ra0 rt2500" | sudo tee /etc/modprobe.d/rt2500
sudo depmod
Reboot your computer once installation is complete. If you get an error complaining about "***/kernel/drivers/net/wireless/rt2x00-legacy/rt2500" or so not being found, dont worry about it.

If your wireless is not "up" or enabled, you can enable it via commandline with:

Quote:
sudo ifup ra0


Please help.  This is driving me nuts.

---

