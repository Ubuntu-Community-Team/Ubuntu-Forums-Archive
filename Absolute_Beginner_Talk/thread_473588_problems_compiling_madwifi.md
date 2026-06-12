---
title: "problems compiling madwifi"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Kossu on 2007-06-14
Hello,

I'm following this guide

```
ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
wget http://patches.aircrack-ng.org/madwifi-ng-r2277.patch
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci

```

at make it returns a few errors
make[3]: ***  [home/ttt/madwifi-0.9.3.1/ath_hal/uudecode] Error 1
make[2]: ***  [home/ttt/madwifi-0.9.3.1/ath_hal] Error 2
make[1]: ***  [_module_/home/ttt/madwifi-0.9.3.1] Error 2

make: ***  [modules] Error 2


at make install it returns

cannot stat 'ath_pci.ko': No such file or directory

Any ideas? :S

thanks

---

### Post by wirelessmonkey on 2007-06-14
After running the patch command, do:
./configure (this may not be necessary, so if it fails, don't worry)
sudo make
sudo make install
sudo depmod -ae


If this doesn't work for you, post more infomation about the errors.  The "make[2]: *** [home/ttt/madwifi-0.9.3.1/ath_hal] Error 2" doesn't actually have any data, the error information is in the output above these declarations.



WM

---

