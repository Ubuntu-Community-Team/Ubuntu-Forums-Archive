---
title: "pppd connection to Internet"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by aleskm on 2006-05-31
Hi,

I've read some instructions how to connect to Internet through my ADSL modem, Ubuntu 6.06 see my ADSL modem, recongizes speed of link, I have configured /etc/ppp/options etc. and I can successfully run the pppd command. I see no error and when I look into /var/log/pppd.log file, is says that i'm connected and tells me local and remote IP address.

Using interface ppp0
Connect: ppp0 <--> 8.48
PAP authentication succeeded
local  IP address 82.202.xxx.xxx
remote IP address 212.90.xxx.xxx

But Firefox doesn't work, I can't ping any web server and I don't know the networking commands in Linux. How can I check if I'm really connected to Internet - where can I see e.g. DNS servers, my IP address, gateway etc. ? Do I need to set up something else to be able to use normal Internet applications (FFox, email, ...) ?



Thx a lot

---

### Post by aleskm on 2006-05-31
I've solved it. The only missing thing was configuration of DNS servers. I don't know why I didn't get this automatically from my ISP  :confused: 

The solution was to install the package _resolvconf_ and then edit the file _/etc/resolv.conf_ and add a line with IP addresses of DNS servers there

nameserver xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy

And then everything started to work :mrgreen:  I'm quite happy, I didn't think that I would be able to get Internet working in Ubuntu with USB ADSL modem (Zyxel 630-C3).

---

