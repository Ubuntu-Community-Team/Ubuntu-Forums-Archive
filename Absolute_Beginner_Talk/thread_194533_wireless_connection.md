---
title: "wireless connection"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2006-06-11
I have installed 6.06 as a partion on one of my systems. I use a usb linksys wireless device on this machine. The XP os works great with this wireless device. The Ubuntu install seems to be just fine, the partioning process worked like a charm. I am using networking under administration to configure the wireless device. I have been to properties and checked the enable this connection box and filled in the other information. However it only lists wep encryption and I have wpa set up. When I have the info entered and am back on the main window and click on activate, the computer freezes and thats that. Any ideas or perhaps Ubuntu will not work with wpa encryption. 
Thanks

---

### Post by oscar on 2006-06-11
I have found that the best way to get wpa working is to use NetworkManager.
```
sudo apt-get install network-manager-gnome
```
This should give you a small notification area applet where you can click, select the network you want to connect to, enter the details and connect to it. The only problem with it is that you have to enter your password every time you reboot in order to connect, though they are working on fixing this with the next release.

---

### Post by Tucatts on 2006-06-11
Many thanks, I will give it a try, sounds like that will work.

---

