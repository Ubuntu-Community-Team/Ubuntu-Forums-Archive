---
title: "Wireless in Gutsy - Look here for instructions"
date: 2007-10-23
forum: Apple Intel Users
---

### Post by alephsmith on 2007-10-23
It would seem that Gutsy and Wireless is the hot issue at the moment- I suggest we make one simple thread with step-by-step instructions about how to get wireless up and going in Gutsy.

Please only post verified instructions. Please be specific so that anyone can follow the instructions.

[SIZE="4"]_**Madwifi for MacbookPro SantaRosa**_[/SIZE]

[LIST=1]
[*]Prepare to build the drivers:
```
sudo apt-get install build-essential 
```
[*]Create a temporary work directory:
```
cd /tmp 
mkdir madwifi
cd madwifi
```
[*]Download the snapshot of madwifi drivers:
```
wget http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2497-20070622.tar.gz
```
[*]Build and install the madwifi drivers:
```
tar -xzf madwifi-ng-r2497-20070622.tar.gz 
cd madwifi-ng-r2497-20070622
make
sudo make install
sudo modprobe ath_pci
```
[/LIST]

---

### Post by msubzwari on 2007-10-23
Dlink GW-510 Rev C works out of the box with Gusty.  It uses rt61-pci module from serialmonkey project.   

I could not get it working with Fiesty.

---

### Post by cyberdork33 on 2007-10-23
Please make sure that you follow the directions in the first section of the madwifi distro documentation if you compile your own madwifi drivers....
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)
>  If you decide you absolutely need to compile madwifi from SVN, then you must **stop the linux-restricted-modules package from providing the madwifi module ath_hal, via its so called volatile module mechanism**. Do so by adding **ath_hal** to the list of **DISABLED_MODULES** in **/etc/default/linux-restricted-modules-common**.

---

### Post by Loki1989 on 2007-10-23
Thank you so much man I have been trying to get the wireless working for so a while after I updated my rc and nothing worked...

---

