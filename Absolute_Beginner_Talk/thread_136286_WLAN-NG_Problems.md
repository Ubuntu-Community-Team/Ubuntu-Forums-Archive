---
title: "WLAN-NG Problems"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by kmansfield on 2006-02-25
I am trying to get wireless networking setup.  I am using the prism2_usb wlan-ng driver on a Mircrosoft MN-510 adapter.  If I disable WEP on my access point and issue the following commands it works:

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="myssid" authtype=opensystem
sudo dhclient wlan0

How do it get all of this to happen automatically when I start the computer?  I have read dozens of posts and get conflicting information.  I created a wlan-conf-xxxx  

I also edited this section with my wep key and ssid

SSID_wlan0="myssid"
ENABLE_wlan0=y
#SSID_wlan1="mywepkey"
#ENABLE_wlan1=n
#SSID_wlan2=""
#ENABLE_wlan2=n

Any help you anyone has would be greatly appreciated...

---

### Post by az on 2006-02-25
[QUOTE=kmansfield]

Any help you anyone has would be greatly appreciated...[/QUOTE]


This device works out of the box for some people.  For those for whom it does not:
[https://launchpad.net/malone/bugs/21569](https://launchpad.net/malone/bugs/21569)

Please add to the bug report.  I'm sure it is a simple fix for somebody, just not me.

---

