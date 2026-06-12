---
title: "Negear n300 dongle = 1mbps DRIVING ME INSANE!"
date: 2012-11-30
forum: Any Other OS
---

### Post by rblockmon on 2012-11-30
Greetings all,
 
Currently I'm running Linux Mint 13 Maya 64-bit. 
 
I installed and setup Netgear N300 wireless dongle, but I only get 1 Mbps speed download and just under for upload. My router is within 15 feet. Anybody had this problem and know a fix?:confused: Any help will be great. I will post my log script when I get home.
 
Best regards, 
Ray

---

### Post by coffeecat on 2012-11-30
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by Pinoy Tux on 2012-12-01
Find the device name for your wireless card; let's presume it's wlan0.  Try the following in Terminal and see if the transfer rate improves:

```
iwconfig wlan0 rate 54M
```If it does, make the change persistent by modifying the rc.local file:

```
gksudo gedit /etc/rc.local
```Add the lines:

```
ifconfig wlan0 up
iwconfig wlan0 rate 54M
```just before the exit 0 line.  Save it and you're done.

---

### Post by UltimateCat on 2012-12-06
I found this thread that another member here Solved his issue with the N300 Netgear issue-

[http://ubuntuforums.org/showthread.php?t=1695036](http://ubuntuforums.org/showthread.php?t=1695036)

And also these links that may be helpful as well-
[http://www.tomshardware.com/forum/38806-42-netgear-n300-wirless-adapter-please](http://www.tomshardware.com/forum/38806-42-netgear-n300-wirless-adapter-please)
[http://code.google.com/p/easy-n300-installer/](http://code.google.com/p/easy-n300-installer/)

	 			 			 				 					 											  	 		[ 			[IMG]https://www.linux.com/media/com_ninja/images/16/page.png[/IMG] 			10 Mar]("https://www.linux.com/community/forums/getting-started-with-linux/n300-wireless-usb-adapter/14411#p14411")Best WiFi resource for linux: [www.linuxwireless.org]("http://www.linuxwireless.org")

HTH

---

