---
title: "Ubuntu PPC WiFi"
date: 2005-01-14
forum: Apple PPC Users
---

### Post by billyfred on 2005-01-14
I'm interested in setting up a G3 iMac to use a D-Link DWL-122 USB wi-fi adapter. Has anyone had any luck doing this? Are the any PPC Linux drivers out there?

Thanks,
BillyFred

---

### Post by chele on 2005-01-14
It should work, using the prism2 modules already in the kernel.

---

### Post by billyfred on 2005-01-14
This network set-up tool does not seem to recognize the device.

---

### Post by nyqo on 2005-01-15
This is what got a DWL-122 working on my iBook:
I installed linux-wlan-ng from universe, modified /etc/wlan/wlan.conf and copied /etc/wlan/wlancfg-DEFAULT to /etc/wlan/wlancfg-"your_ssid_here" and edited that accordingly. I then created the following script to run whenever I need it:


#!/bin/sh

sudo modprobe prism2_usb
sudo rmmod prism2_usb
sudo modprobe prism2_usb prism2_doreset=1
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="your_ssid_here" authtype=opensystem
sudo dhclient wlan0

I am up and running, hope this helps you.

---

### Post by billyfred on 2005-01-15
Thanks, I'll give it a try.  BTW, where do you save the script?

---

### Post by billyfred on 2005-01-22
[QUOTE=nyqo]This is what got a DWL-122 working on my iBook:
I installed linux-wlan-ng from universe, modified /etc/wlan/wlan.conf and copied /etc/wlan/wlancfg-DEFAULT to /etc/wlan/wlancfg-"your_ssid_here" and edited that accordingly. I then created the following script to run whenever I need it:


#!/bin/sh

sudo modprobe prism2_usb
sudo rmmod prism2_usb
sudo modprobe prism2_usb prism2_doreset=1
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="your_ssid_here" authtype=opensystem
sudo dhclient wlan0

I am up and running, hope this helps you.[/QUOTE]

The above advice worked just fine, but I found that I had to execute the "sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable" line twice to get the interface up.

---

### Post by ssam on 2005-01-22
does the DWL-122 work well once its going?
i am thinking of getting one.

thanks

ssam

---

### Post by billyfred on 2005-01-23
[QUOTE=ssam]does the DWL-122 work well once its going?
i am thinking of getting one.

thanks

ssam[/QUOTE]

I find that range is a problem with the DWL-122. On my son's eMac, running OS 10.2x, and being close to the wireless router, it seems quite stable. On an iMac in the basement, running Ubuntu Hoary and being rather far from the router, it seems unstable and slow. I'm going to see about getting a LinkSys WUSB-12. It's clunkier, but it has better range. I think it's also based on the Prism 2/3 chipset.

billyfred

---

