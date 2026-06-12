---
title: "Unable to connect to the internet"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by A_T on 2007-03-31
My computer uses a usb dongle (zd1211) to connect to a wireless router. Ubuntu recognises the dongle fine, and I have enabled it under Networking (DHCP) but when i fire up Firefox I cannot connect to the internet or even the router using 192.168.1.1. I have a dynamic IP address.

Can anyone help?

---

### Post by victorbrca on 2007-03-31
Does the following code returns anything??

> sudo iwlist scanning


Vic.

---

### Post by Terry851 on 2007-03-31
I'm a new Ubuntu/Linux user, so may not be the best person to respond to your note, but I just got my wireless working.  For me, key was to blacklist ipv6.

I suggest you let other experts guide you in getting your dongle working, but if you want to quickly test this out:

Applications, Accessories, Terminal:
sudo gedit /etc/modprobe.d/blacklist

add to bottom of file:
# disable ipv6 (TESTING); may be required for wireless access?
blacklist ipv6

save the file and reboot.  If it works, great!  If not, simply edit the file and remove the lines you added.

Good luck!

---

### Post by zvacet on 2007-04-01
In DNS tab I belive you will found your router address.Replace it with your nameservers.After that 
```
pppoeconf
```

---

