---
title: "Internet connection problem"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Klayy on 2007-05-14
Hello, Ive installed Ubuntu 7.04 x64 from the alternate cd, this is a laptop (asus f3jp)
and I need to connect to the internet to get updates and stuff for the ati x1700 (and other stuff of course)

My connection is through LAN in a dorm, we all get assigned an IP, and it is locked for a certain MAC, so I cant go dhcp
I found a site online 
([http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)) with a guide on how to change the ip, subnet mask, gateway and dns
I did those changes, Im sure Ive saved it, I can ping everything ive tried (i mean local, not internet), but when I run apt-get update, each line goes failure
where can the problem be?

also I was a bit confused on what these lines mean

network 192.168.1.0
broadcast 192.168.1.255

what are they?

thanks a lot

---

### Post by Klayy on 2007-05-14
problem resolved :)
I needed two reboots for some reason

---

### Post by dstew on 2007-05-14
Those IP addresses are for a local network, such as when you have your own router. At your university, your addresses will be different. You need to get them from your network administrator, and put the correct values into your interfaces file.

---

