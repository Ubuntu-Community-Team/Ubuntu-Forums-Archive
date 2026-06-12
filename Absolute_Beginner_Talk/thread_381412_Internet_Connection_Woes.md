---
title: "Internet Connection Woes"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by mbm8e on 2007-03-10
I just installed Ubuntu yesterday at home on my Dell Latitude D800. I was able to connect to the internet through both ethernet and wireless. However today when I returned to my apartment at school when I plugged in my ethernet cable I could not get on the internet. From the properties menu it looks as if it is receiving packets but not sending them out. The internet at my apartment complex is included, and all I'm doing is plugging my cable into the wall. Any Ideas?

---

### Post by hod139 on 2007-03-10
For wired what does typing ifconfig into a terminal produce?  You should hopefully see an assigned IP address.   I"m assuming the network is dhcp, in which case you can try and request a new IP by typing the following into a terminal
```

sudo dhclient eth0

```


Note, the eth0 may be slightly different on your machine (i.e. eth1).   The previous ifconfig command should help you figure out what the device name is if it isn't eth0.  

For wireless you use the command iwconfig to find the device name, and renew using the same dhclient command.

---

