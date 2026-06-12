---
title: "Automatic Network Start"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by bmachia on 2008-03-16
I just figured out how to enable WPASupplicant on my laptop and connect to my local router (securely).

Everything works fairly smoothly.  But each time I boot/login to the Laptop I do not have network connections until I type;
	sudo /etc/init.d/networking start 	..or.. restart

Can someone tell me what I need to do to have my Laptop AUTOMATICALLY connect  at login with the WPA Router with out the manual typing of sudo /etc/init.d/networking start?

Bill

---

### Post by tommcd on 2008-03-16
See this guide on wpa:
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29)

---

