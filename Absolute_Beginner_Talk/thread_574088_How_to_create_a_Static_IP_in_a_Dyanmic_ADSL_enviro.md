---
title: "How to create a Static IP in a Dyanmic ADSL environment?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by jmkhoo on 2007-10-12
Hi, in my country, home users are not able to get a static IP from the ISPs and all home users are using Dynamic ADSL which does not assign any Static IP. Is there any way to create a Static IP myself so that I am able to host my own server in my home and broadcast it ?

---

### Post by nest on 2007-10-12
[no-ip]("http://www.no-ip.com/")

No-IP is a dynamic dns provider (ddns).

---

### Post by bvmou on 2007-10-12
no-ip or dyndns.com will give you a free dynamic account that will give you a persistent name tied to your changing local IP address.  You can update their servers either with your router (and if support is not built in it may be supported by ddwrt or OpenWRT) or with the package ddclient.  If you are behind a router do not go with the ddclient defaults, the automatic configuration may not work as well as following the instructions and using a web service to confirm your public IP address.  This is an incredibly handy thing for hosting or just having an ssh server etc.

---

