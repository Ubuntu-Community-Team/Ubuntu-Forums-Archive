---
title: "bcm43xx driver help"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by android mouse on 2007-03-17
I finally got my wireless card working using ndiswrapper only to find out that it doesn't support monitor mode which I need. So now I'm trying to get the native bcm43xx driver to work.

I know I've done something right because when the bcm43xx driver is loaded and I run 'iwlist scan' it lists the local APs around me. The problem is it won't connect to anything. I've set my ssid with 'iwconfig eth1 essid x' but everytime I run 'dhclient eth1' it times out and doesn't get assigned an ip. WEP and WPA are disabled on both my computer and the AP so that isn't the issue. 

I've also made sure the firmware was properly extracted and have both used the installed script and done it manually just to make sure. What could the problem be?

thanks

---

### Post by xopher on 2007-03-18
I'd suggest to for you to try out network-manager, it's great, graphical and above all, WORKS. :)

It automatically detects all available AP's, and connects to the best one (if you have permission to access it of course)

```
sudo apt-get install network-manager
```

---

