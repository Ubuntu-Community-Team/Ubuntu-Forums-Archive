---
title: "Install ATI Drivers for Radeon X850XT"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by DADDA on 2006-09-26
Hi,

I have a ATI RADEON X850XT video card. And when I just installed Ubuntu 6.06, the X-server will not start?

How do I install the ati drivers, and also correct the settings for my monitor... 

I have been searching on the web for some answears but I don't realy now wich is the correct?

Please help me... Iam still just a noob, and with out 'X' iam pretty lost. 

Thanks for everything...

---

### Post by davebgimp on 2006-09-26
Check out this wiki page for info on installing the ATI drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=show&redirect=BinaryDriverHowto%2Fati](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=show&redirect=BinaryDriverHowto%2Fati)

Since you can't boot X, do whatever you need to do from the wiki page in Single User Mode. When you first boot and see the Grub menu, select the second from the top in the list you have, it'll be called "Single User Mode". That will boot you to a command line, running as root (so be careful). Do what you need to do and then reboot to the normal mode and see if it works.

---

### Post by pay on 2006-09-26
without X you'll have to do it with the terminal
Typ```
sudo nano /etc/default/linux-restricted-modules-common
```and change```
DISABLED_MODULES=""
```to```
DISABLED_MODULES="fglrx"
```then download the Ati drivers```
wget http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.29.6.run
```then uncomment (remove the #) from the universe and multiverse repositories in the /etc/apt/sources.list```
sudo nano /etc/apt/sources.list
```then download the dependencies```
sudo aptitude update
sudo aptitude install module-assistant build-essential 
sudo aptitude install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
```create packages```
bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
```install packages```
sudo dpkg -i xorg-driver-fglrx_8.29.6-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.29.6-1_i386.deb
sudo dpkg -i fglrx-control_8.29.6-1_i386.deb
```Remove any old fglrx debs from ```
sudo rm /usr/src/fglrx-kernel*.deb
```Compile the kernel module```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```Update the xorg.conf file```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```Reboot```
sudo shutdown -r now
```

Shamelessly copied from [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
Goodluck

---

