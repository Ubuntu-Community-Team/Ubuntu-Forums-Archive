---
title: "Kernel issues"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by kokobean on 2006-10-02
I am trying to install my wireless card (Broadcom BCM4306). I have been following these instructions to compile my kernel [http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

These are the instructions I found online for the Broadcom card:
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo apt-get install linux-headers-2.6.10 (whatever version)
cd /usr/src/
sudo tar xvzf ndiswrapper-1.2-rc1
cd /usr/src/ndiswrapper-1.2-rc1/
sudo make
sudo make install
cd /the dir where your windows networkdrivers are/
sudo ndiswrapper -i bcmwl5 (or other driver name if you have another card)
sudo ndiswrapper -l (making sure the driver is installed)
sudo modprobe ndiswrapper
sudo dmesg (you sould see that the card is installed)
sudo iwlist wlan0 scan (to get a list of APs)
sudo ndiswrapper -m (ndiswrapper will now be loaded automatic at bootup)

I make it as far as make install and get "No rule to make target 'init.main.o', needed by 'init/built-in.o'. Stop." From some googling it seems that I needed to compile my kernel, which I tried to do following the link posted above. I can't seem to get the linux-tree from synaptic or install it from a website either. Plus, due to a typing error, when I get to the command:

sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

I forgot the "-" before custom and when I try to run the command correctly I get an error saying it did not match expectations and get the "no rule to make target 'init/main.o" error.

Please help! I've done so much tweaking that I'm not sure where to start to fix it...

---

### Post by kokobean on 2006-10-02
I misspoke- when I type "sudo make install" the error is "cannot stat 'loadndisdriver.8': No such file or directory"

---

