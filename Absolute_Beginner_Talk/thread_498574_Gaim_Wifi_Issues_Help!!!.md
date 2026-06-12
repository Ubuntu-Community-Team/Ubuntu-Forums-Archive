---
title: "Gaim Wifi Issues Help!!!"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by hiltonman78 on 2007-07-11
Hi I just got the drivers on my dell installed and just got the wifi working as well. My problem is that the gaim doesn't seem to think it can connect or doesn't see the connection. Not really sure what it thinks. All I know is when I use the wifi radar to connect to the internet gaim will not connect. It opens. It shows up but for some reason will not connect. My computer is a dell b130. I am running a broadcom chipset.


brett@brett-laptop:~$ lspci | grep Broadcom\ Corporation
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I looked around on forums and did not see this issue with anyone else. I am using wifi radar as my wireless connection program. Any help would be appreciated thanks. Brett

---

### Post by ugm6hr on 2007-07-11
I am no expert - but I have a couple of things worth trying.  This assumes you can get online with a browser.

In GAIM:

1.  Preferences (Tools Menu):
Go to Network tab and make sure the auto-detect IP address is ticked.

2.  If you are using MSN account - Edit the account, and select Use HTTP method in Advanced tab.

Hope one of those helps.  If not - I don't know.

---

### Post by hiltonman78 on 2007-07-12
Thanks I will give that a try.  Never hurts to try.  Brett

---

### Post by twiceasworn on 2007-07-12
Just to clarify, you are able to get to a browser and surf the web?  If that is the case then I would definitely check the connection settings on Gaim.

---

### Post by hiltonman78 on 2007-07-13
Yes I get a connection on my Wifi Radar.  It shows the ip address of my wireless router and I can also search the web.  I click on Gaim and it pulls up but will not connect.  I checked the settings like the person in the first post said to do and it seemed all fine.  Maybe there is something else I am missing or a something is out of wack?  I am very new to ubuntu so any ideas no matter how small may help.  Thank You, Brett

---

### Post by hiltonman78 on 2007-07-16
Not to worry folks.  I found a great solution to my problem.  Its called Kopete.  And it works wonders so don't worry about this issue its solved.  Thanks

Brett

---

