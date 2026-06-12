---
title: "dwl-122 wlan-ng 2.6.10 problems"
date: 2005-04-11
forum: Apple PPC Users
---

### Post by danns on 2005-04-11
After upgrading to hoary the /etc/init.d/wlan nor the provided rc.wlan script work.  The error I get is this:

Starting WLAN Devices: FATAL: Module wlan0 not found.
 
for /etc/init.d/wlan

and 

Starting WLAN Devices:FATAL: Module wlan0 not found.
/sbin/prism2dl not found, aborting firmware download.

for the rc.wlan provided by linux-wlan-ng documentation.

I'm not surprised because I had this same problem on slackware with the 2.6.10 kernel.  Manually configuing the card works and since I am using wep I managed to piece together a script (culled from reading the docs, wlanctl-ng command reference, my conf files and /etc/wlan/start) that seems to work for me:

----------------------------------
#/bin/bash

rmmod prism2_usb
modprobe prism2_usb prism2_doreset=1
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0=mykey
wlanctl-ng wlan0 lnxreq_autojoin ssid="gehenna" authtype=sharedkey
dhclient3 wlan0
------------------------------------

If anyone has any improvments or suggestions I'd be open to hearing them.

---

