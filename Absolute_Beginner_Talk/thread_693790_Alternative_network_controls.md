---
title: "Alternative network controls?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2008-02-11
I was wondering if there is something I can use to only allow certain MAC addresses on my WiFi and view IP's which are connected to the network and perhaps boot them off.

Whats cool and spiffy? maybe like a radar thing... and a list of peoples using your wireless...


thanx
SV

---

### Post by dca on 2008-02-11
Add a wireless router and use the admin web portal for config...  The owner's manual of each explains what the default IP address is is for access...

---

### Post by staticvoid on 2008-02-11
ok, thanks, but is there some app I can use to kick people off my network or only allow certain MAC addys? I didn't know the 192.168....web portal could do this, view whoes sucking your wireless.



Thanks

sv

---

### Post by staticvoid on 2008-02-12
bump

---

### Post by hyper_ch on 2008-02-12
you should be able to filter by mac addresses. BUT a mac address can easily be faked.

---

### Post by oedha on 2008-02-12
what did you use for your wireless ? access point or wireless router ?
they have their own setup menu to allow only your mac to use the access

---

### Post by staticvoid on 2008-02-12
I have a wireless router that connects to an ADSL modem, I have it all configed, its unprotected, not sequirity, but I would like to view the IP addresses of the people using it. Is this posible?

sv

---

### Post by hyper_ch on 2008-02-12
depending on the software that's on your modem it is possible... you could also use kismet to find out what wireless devices are connected to which access points - but that would not give the IP of the deivces, just their mac numbers.

---

### Post by staticvoid on 2008-02-12
aha! kismet, thank you :)

---

### Post by hyper_ch on 2008-02-12
or aircrack... not sure which one it is... I think kismet only shows wifis and with aircrack you can see who is connected to each one...

---

### Post by staticvoid on 2008-02-12
kismet says it does intrusion detection, how can I get that to work? I remember using an open wireless on the street and someone kicked me off or blocked my MAC addy or something.. some people in my house cannot connect to our internet when it is wpa or wep protected, its wierd, so i would still like to have some sort of way to block intruders...something like

kismet -block hostname "ubuntu" -rightNow

?

tnx

sv

---

