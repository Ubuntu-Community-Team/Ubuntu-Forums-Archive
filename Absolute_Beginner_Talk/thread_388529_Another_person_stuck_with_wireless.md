---
title: "Another person stuck with wireless"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by paulmat on 2007-03-19
You probably get fed up with the amount of people asking this kind of thing, but i've been trying to connect to my wireless router, and am getting completely stuck.

My USB adapter is a D-Link DWL122, and i've installed the linux-wlan-ng drivers. I then tried to set it up through the network admin, but I really didn't have a clue what I was doing. I've tried the DHCP connection, and i've tried setting a static IP, but neither of them have worked. 

A big problem I have is that I don't know my network password (if there is one). Is there any way I can find it through Windows?

Can anybody help me? :p :p

---

### Post by Kobalt on 2007-03-19
If there is a place where you should be able to set up your network password it's in the config of your router. You can do that either from windows or from Ubuntu, by entering in firefox' address bar : 192.168.0.0
You should access your router and its setup. I suggest you chose a WEP key the longest possible (26 characters, in hexadecial), give your network an ESSID, and set your connection in dhcp. 
Once you've done that, right-click (in Ubuntu now) on the network-monitor icon in the right top corner of your screen and select Configure, and set up your network accordingly to what you've set previously into your router.

---

### Post by paulmat on 2007-03-19
Hmm. I typed the address, but it just came up with a problem loading page.

---

### Post by Kobalt on 2007-03-19
Then you should report to your hardware's manual to know how to access the configuration tool of it...

---

### Post by teaker1s on 2007-03-19
most router management ip and logon default settings on label underneath

---

### Post by paulmat on 2007-03-19
Ah cool. I'll have a look.

---

### Post by dstew on 2007-03-19
Of course, you didn't try to connect to 192.168.0.0 by wireless, did you? Since you don't have a wireless connection yet, that probably would not work. You have to plug in an ethernet cable to reconfigure the router.

---

### Post by UberSoldAt666 on 2007-03-19
I thought I would add that not all routers are 192.168.0.0. In example  mine is 192.168.2.1 . Log in to windows and double click on the computer with the three green waves to the right. Then click on support to get the routers IP.

Beyond that I can't help you because I am waiting to get a compatible Wireless card for my extra comp that didn't have one in the first place. Good luck!

---

