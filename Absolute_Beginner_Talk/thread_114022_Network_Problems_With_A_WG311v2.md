---
title: "Network Problems With A WG311v2"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by Big Pat on 2006-01-07
Nevermind I figured out I'm a idiot. I wasn't using the driver I was using autorun.inf. Then I saw the folder named driver.... and I thought ya... I am dumb!

I've just installed ubuntu ver. 5.10-i386 and I'm trying to install a netgear WG311v2 network card. This is my first exparament into linux, so I know very little. I've been following [these]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Complete_Example_1_-_Netgear_WG311v2_.2B_Ndiswrapper_.2B_Ubuntu.2FDebian_.28Post_by_Yueh_-_stevenyu24_AT_gmail.com.29") instructions, but the file paths are diffrent in those instructions from what I see on the computer. I think I found the right place, and tried to install the drivers but all the drivers I tried, when i check them, say:
```
Installed ndis drivers:
autorun invalid driver!
``` I have tried all the drivers on the netgear site. I figured I've done something wrong so I thought I would ask. So what do I need to do tho get it to work?

---

### Post by Sef on 2006-01-12
Here's a post in Linuxquestions that may help you:

> Would you recommend the product? yes | : Not Indicated | Rating: 9


Kernel (uname -r): 	2.6.8-2-k7 	
Distribution: 	Debian 	
Used dselect to obtain ndiswrapper and got WinXP drivers from NetGear site.

su -
&lt;password&gt;
ndiswrapper -i /path/to/inf/file
modprobe ndiswrapper
iwconfig wlan0 channel x
iwconfig wlan0 essid NETGEAR

connected? Type ndiswrapper -m

If you used a NIC to download software, feel free to disable or remove and use ifconfig to uninstall or just edit your /etc/network/interfaces file

Done

Link: [http://www.linuxquestions.org/hcl/showproduct.php/product/1731/sort/2/cat/149/page/1]("http://www.linuxquestions.org/hcl/showproduct.php/product/1731/sort/2/cat/149/page/1")

---

