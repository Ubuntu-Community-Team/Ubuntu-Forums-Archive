---
title: "Atheros AR5006EG on 7.10"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2007-11-27
Hi,
I've got a megabook pr210 (amd 64). I can't see the wireless card on the network manager.
It's a Atheros AR5006EG.
Could you help me to install it?
Thanks,

---

### Post by stchman on 2007-11-27
> **linux-beginner said:**
> Hi,
I've got a megabook pr210 (amd 64). I can't see the wireless card on the network manager.
It's a Atheros AR5006EG.
Could you help me to install it?
Thanks,

Did you enable the Restricted Driver?

---

### Post by linux-beginner on 2007-11-27
I think I do. How can I check it?

---

### Post by stchman on 2007-11-27
> **linux-beginner said:**
> I think I do. How can I check it?

System--->Administration--->Restricted Drivers Manager.

Once this is up check to see if the Atheros HAL is enabled.

---

### Post by linux-beginner on 2007-11-27
it's enable!

---

### Post by stchman on 2007-11-27
Then in your system try there is an icon that you can click on that should drop down a list of available wireless networks.

Click one to connect.

---

### Post by linux-beginner on 2007-11-28
Could you tell me where system try is?

---

### Post by stchman on 2007-11-28
> **linux-beginner said:**
> Could you tell me where system try is?

Sorry I misspelled.  It is the system tray.  By default it is in the upper right corner next to the clock.

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

This pic should help.

---

### Post by Petrek on 2008-04-15
I fixed it this way (now it is ok, I'm using WiFi+WPA):

1: disable the restricted atheros driver
2: run terminal
3: run this on terminal:
wget -c [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
tar xvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007

sudo apt-get update && sudo aptitude install build-essential

sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

4: restart computer

---

