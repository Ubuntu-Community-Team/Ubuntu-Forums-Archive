---
title: "Problems with wireless usb/connecting to network"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by rhoule on 2006-03-16
Hi all, well back again.... 

Earlier today i installed linux-wlan-ng drivers for my wireless usb device.
I rebooted and it showed the usb device as wlan0, so i proceeded to try 
and get it working with my network, but i was having no luck.
So i took a 2 or 3 hour break and rcame back to try what i learned on [https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)
and when i came back my wlan0 was gone, so i unplugged the usb and plugged it back in and it came back....
I proceeded with the ubuntu wifi how to guide.. and was having no luck so i rebooted and my wlan0 disappeared again after reboot.. this time i can't get it back by plugging and unplugging the usb..

any ideas what this could be? so frustrated right now :confused:

---

### Post by poofyhairguy on 2006-03-17
I have fought with a Prism 2 usb device (which I bet is what you have) for days with Ubuntu. I have found two good options:

1. Use Ndiswrapper. Guide is here:

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

2. Use another distro. I hate to say it, but for some reason SUSE does not seem to have the same problems with these devices.

---

### Post by rhoule on 2006-03-17
Ok thanks I'm glad to know its not just me i thought i was just too slow to figure this out..

I'll try the Ndiswrapper, i've been thinking of that anyways, and if i have no luck i'll give SUSE a shot.

Thanks again.

---

