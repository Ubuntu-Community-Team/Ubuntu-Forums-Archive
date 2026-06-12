---
title: "Internet connection share with iphone"
date: 2011-11-28
forum: Apple Hardware Users
---

### Post by whynot on 2011-11-28
Hi everbody
I have iphone 4 cell phone and ubuntu 11.04 64x internet connected computer system. Is it possible to share this internet connection via usb-cable with iphone?
Thanks for any help.

---

### Post by collisionystm on 2011-12-01
> **whynot said:**
> Hi everbody
I have iphone 4 cell phone and ubuntu 11.04 64x internet connected computer system. Is it possible to share this internet connection via usb-cable with iphone?
Thanks for any help.

No

you need a wireless router

---

### Post by abhilash29 on 2011-12-11
No idea about a USB connection sharing, however you can create a wireless connection by clicking on the NM applet over the top right and select "Create new wireless network". After that just enter the name for the connection, type of security (Open/WEP/WPA, etc) and click "create". Then you can navigate to the wifi settings and select the wifi that you created on ubuntu. :)

---

### Post by whynot on 2011-12-12
> **abhilash29 said:**
> No idea about a USB connection sharing, however you can create a wireless connection by clicking on the NM applet over the top right and select "Create new wireless network". After that just enter the name for the connection, type of security (Open/WEP/WPA, etc) and click "create". Then you can navigate to the wifi settings and select the wifi that you created on ubuntu. :)

thanks but my wifi doesn`t work at all. I need to use over 3g or usb cable. 3g works but i don't have that cell support.So all that remains is to via usb cable.I red about this [N900]("http://wiki.maemo.org/N900_USB_networking") article it could be a solution for me. And Ubuntu 11.10 detects iphone cable connection as eth1. So i think i have to change some things in iphone 4 (JB).

I use those commands for ubuntu
```

#!/bin/bash
sudo iptables -A FORWARD -o eth0 -i eth1 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

```
I think i just need to give some ips like ip for iphone and default router ip.
In iphone its not that easy i guess. 

Thanks.

---

