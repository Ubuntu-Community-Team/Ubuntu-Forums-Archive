---
title: "trouble connecting to a home network"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by kaboom on 2007-05-17
Hey all
im trying to connect to a wireless network.  Our provider is comcast.  In system>admin>networking i seem to be  picking up my wireless card as wlan0 so i dont think its a hardware problem.  I am also pretty sure i have the configuration right because my roomate is online with his windows box and I setup his using the same info.  I cant see anything else that may be causing me not to pick up the internet.  

Any ideas?  Is there a way i can scan to see if I am even getting the signal? (im thinking of a counterpart to windows view available wireless networks).  

thanks for the look
chris

---

### Post by Bachstelze on 2007-05-17
First, if your wireless card *really* detected ?

```
sudo iwconfig
```

If you get an entry that doesn't say "no wireless extensions", that's the one. Then, to show all available networks, you can do

```
sudo iwlist wlan0 scan
```

it will return a list of all available networks. To connect to one, just do

```
sudo iwconfig wlan0 essid YOUR_ESSID key YOUR_WEP_KEY
```

then, assuming your network runs DHCP :

```
sudo dhclient wlan0
```

And you're there :)

---

### Post by kaboom on 2007-05-17
thanks hymn that did the trick

---

