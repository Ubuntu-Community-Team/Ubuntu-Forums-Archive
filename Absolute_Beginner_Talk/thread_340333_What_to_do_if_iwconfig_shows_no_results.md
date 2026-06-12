---
title: "What to do if iwconfig shows no results?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Winterkind on 2007-01-17
Hello!

I am trying to set up my WLAN network after a fresh installation of Ubunto 6.10. While reading through the WPA how-to guide ([https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)) I came across an instruction to execute "sudo iwconfig" to check if my wireless device is working. This is the output:

> lo: no wireless extensions.

eth0: no wireless extensions.

sit0: no wireless extensions.

wlan0: no wireless extensions.

Doesn't look so good to me. Unfortunately the guide does not give any instructions in such a case. Any hints?

I am using the USB stick D-Link DWL-122 and installed the drivers as described in the community hardware guide.

Thanks!

---

### Post by Riyonuk on 2007-01-17
Well it means no device is configured yet. How did you install the drivers, by using ndiswrapper? Did you try the settings in System > Administration > Networking?

---

