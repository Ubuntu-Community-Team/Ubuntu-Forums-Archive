---
title: "Wireless not working"
date: 2008-08-30
forum: Apple Hardware Users
---

### Post by mwcurry on 2008-08-30
I tried to setup my wireless (as per [https://help.ubuntu.com/community/MacBook#Wireless](https://help.ubuntu.com/community/MacBook#Wireless)) but it will not detect a wireless network.  I'm rather new to Linux in general and would like some help setting it up.

Relevant info:
MacBook 2.1
Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)

(On a side note: I also can't get "right click" to work)

Thanks

---

### Post by cyberdork33 on 2008-08-31
please give output of 
```
ifconfig
```
and
```
lsmod |grep ath9k
```

---

### Post by mwcurry on 2008-08-31
ifconfig yeilds:
eth0      Link encap:Ethernet  HWaddr 00:19:e3:44:43:56  
          inet addr:172.17.32.254  Bcast:172.17.33.255  Mask:255.255.254.0
          inet6 addr: fe80::219:e3ff:fe44:4356/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3478996 (3.3 MB)  TX bytes:265661 (259.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87100 (85.0 KB)  TX bytes:87100 (85.0 KB)

lsmod |grep ath9 yields:
ath9k                 266680  0 
mac80211              221556  1 ath9k

---

### Post by Rog-Mahal on 2008-08-31
I have the same card in a 3rd gen. Macbook, and I installed the madwifi drivers with no problem. The version that has been the most stable for me is madwifi-ng-r3545-20080416.tar.gz which you can find [here]("http://snapshots.madwifi.org/madwifi-trunk/")

Instructions are included for how to install, if you need any additional help, just post here. 

Installing this way worked for me, but I don't know anything about the ppa package you downloaded and installed, perhaps cyberdork could speak to that, i wouldn't want this solution to complicate the issue further by breaking anything.

---

### Post by cyberdork33 on 2008-08-31
> **Rog-Mahal said:**
> Installing this way worked for me, but I don't know anything about the ppa package you downloaded and installed, perhaps cyberdork could speak to that, i wouldn't want this solution to complicate the issue further by breaking anything.
ath9k is the driver that will be replacing madwifi in the near future.

mwcurry, I don't know what the issue is. It looks like things are in order. ath9k is still in major development so it might be best to stick with the older madwifi driver for awhile longer.

---

### Post by mwcurry on 2008-09-01
I cannot figure out how to properly configure and get the madwifi drivers to work with wicd.  I've tried a few times but do not know what is wrong.  At one point, when I uninstalled wicd and reinstalled the default network manager, the default network manager was ABLE to see the wireless networks around me, but wicd wasn't.

Any idea why this might be?

---

### Post by hanzomon4 on 2008-09-01
I'd use ndiswrapper and the windows driver. I tried ath9k but it gave problems, like not being able to connect. I could find the version of madwifi that worked on my system, it's not the latest svn but an earlier revision of svn.

I didn't even know I could use ndiswrapper but it was easy to setup and worked without a hitch.

---

### Post by mwcurry on 2008-09-01
How could I get access to ndiswrapper and the windows driver? In the macbook guide, it says that it is on the Leopard CD, which I left back home.  I have no way of getting my hands on a physical Leopard disc.

---

### Post by mwcurry on 2008-09-02
Interesting update.  If I put wlan0 instead of ath0 in wicd, I am able to SEE wireless APs, but I cannot connect to them (it is always trying to obtain  IP address).

---

### Post by flaggh on 2008-09-02
I have the same wifi card as you and have had success with both madwifi and ath9k but they both have their issues.  Madwifi intermittently stops working but recovers if I briefly suspend.  Ath9k has causes lockups on my computer.  One poster observed that the lockups consistently occur if you suspend twice but I haven't confirmed this, not wanting to lock up my computer.

I was using r3358 of the madwifi drivers. The latest build would not work.  The instructions on this post worked for me:[http://ubuntuforums.org/showpost.php?p=4825026&postcount=1]("http://ubuntuforums.org/showpost.php?p=4825026&postcount=1")

Are you using the latest version of Wicd?  The one in their repo is 1.4.2, but the latest stable release is 1.5.1 and works much better.  It can be found at [http://www.wicd.net/latest]("http://www.wicd.net/latest")

---

### Post by mwcurry on 2008-09-02
I tried the instructions linked and when I do iwconfig, I do not get ath0, I get wlan0.

How would I uninstall all the wireless drivers so I could try fresh?

---

### Post by flaggh on 2008-09-02
before you uninstall, try:
```
sudo modprobe -r ath_pci
sudo modprobe ath_pci
```
if this does not work you can try to uninstall by changing into the install directory and running make uninstall:
```
cd /madwifi/directory
sudo make uninstall
```

---

### Post by cyberdork33 on 2008-09-02
I would disable ndiswrapper while you are at it so that you are working with only one driver at a time:
```
sudo modprobe -r ndiswrapper
```

---

### Post by mwcurry on 2008-09-02
None of this is working.  Does anyone know why the wireless is showing up as wlan0 instead of ath0, as described in most of the guides I've read.

---

### Post by flaggh on 2008-09-02
Did you perhaps already install the ath9k driver?  If you did then it would show up as wlan0.  In the menu bar go into System -> Administration -> Hardware Drivers and post what is listed under there.

---

### Post by mwcurry on 2008-09-02
Yes I already installed ath9k.  It said to on the community macbook page. Under Hardware Drivers, it says "No proprietary drivers are in use on this system" and under that it says Device Driver: Suppor for Atheros 802.11n wireless LAn cards.  Enabled (checked) and Status (In Use)

---

### Post by flaggh on 2008-09-03
Then you don't need ndiswrapper or madwifi.  Just uninstall the both of those and you should be ready to go.  If that doesn't work, uncheck and then recheck the "Support for Atheros 802.11n wireless LAN cards" and reboot your computer.  In the Wicd preferences you should be using the wext WPA supplicant driver and the wireless interface should be set as wlan0.  If you have any weird characters in the WPA passkey you may have some problems, but other than that, everything should work after that.

---

### Post by mwcurry on 2008-09-03
Thanks.  How can I check to make sure I only have the ath9k drivers installed and ndiswrapper is not enabled?

---

### Post by cyberdork33 on 2008-09-03
> **mwcurry said:**
> Thanks.  How can I check to make sure I only have the ath9k drivers installed and ndiswrapper is not enabled?
To remove the driver that ndiswrapper is using, do
```
sudo ndiswrapper -l
``` (that is a lowercase L not an I) That will list the drivers you have installed. To remove a driver use:
```
sudo ndiswrapper -r *driver_name*
```

---

### Post by mwcurry on 2008-09-03
When I do the command ```
sudo ndiswrapper -l
```, I get the message: no ndiswrapper utils found!

---

### Post by cyberdork33 on 2008-09-03
> **mwcurry said:**
> When I do the command ```
sudo ndiswrapper -l
```, I get the message: no ndiswrapper utils found!In that case, I would guess that you never had ndiswrapper working.

---

### Post by mwcurry on 2008-09-04
So if it isn't working and only ath9k is installed, why isn't wicd letting me connect to wireless?

---

### Post by cyberdork33 on 2008-09-04
> **mwcurry said:**
> So if it isn't working and only ath9k is installed, why isn't wicd letting me connect to wireless?
ath9k is still under heavy development. It is very new. there are likely problems with it. also, if you have tried to install madwifi along with ath9k, then they will also conflict.

---

### Post by flaggh on 2008-09-04
I would check your Wicd configuration.  Make sure you are using wext, the correct wireless interface, you have the right type of encryption set, and the password isn't misspelled.  What is the output of:
```
iwconfig
```
and
```
iwlist wlan0 scanning
```

---

