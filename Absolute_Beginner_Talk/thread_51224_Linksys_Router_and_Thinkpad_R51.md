---
title: "Linksys Router and Thinkpad R51"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by Snodgrass on 2005-07-23
I've just installed Ubuntu 5.04 on a Thinkpad R51.  It's beautiful, and I'm so grateful to Ubuntu.  The only problem is getting wireless to work.  From System->Administration->Networking I am now told 

Wireless Connection 
the interface ath0 is active

In its Properties I've put the SSID name and WEP key I registered with Linksys when the Thinkpad was running Windows XP. I went over to 192.168.1.1, the Linksys registration page, and poked around there but didn't see anything I thought could help.

It's configured for DHCP, and there are two DNS servers from my ISP.

The IBM wireless icon glows promisingly, and so does the Linksys WRT54G monitor.

But as soon as I remove the cable connection from Linksys to the Thinkpad, the connection is broken.  

A hundred dollar donation to Ubuntu for information leading to a solution.

TIA,

Snod

---

### Post by scoon on 2005-07-23
Hey there, 

Make certain that you key is correct and that it does not need to be prefaced w/ 0x.

regards,
 scoon

---

### Post by Snodgrass on 2005-07-30
There's a nice Catch-22 here. Now that I've ripped out Windows, I can't access the Linksys URL that has the WEP information. I'll have to find a Windows machine, or wait for the Ubuntu Linux installfest that's scheduled for September, or find the information I need on one of these nifty bulletin boards. /Snod

---

### Post by poofyhairguy on 2005-07-30
[QUOTE=Snodgrass]I've just installed Ubuntu 5.04 on a Thinkpad R51.  It's beautiful, and I'm so grateful to Ubuntu.  The only problem is getting wireless to work.  From System->Administration->Networking I am now told 

Wireless Connection 
the interface ath0 is active

In its Properties I've put the SSID name and WEP key I registered with Linksys when the Thinkpad was running Windows XP. I went over to 192.168.1.1, the Linksys registration page, and poked around there but didn't see anything I thought could help.

It's configured for DHCP, and there are two DNS servers from my ISP.

The IBM wireless icon glows promisingly, and so does the Linksys WRT54G monitor.

But as soon as I remove the cable connection from Linksys to the Thinkpad, the connection is broken.  

A hundred dollar donation to Ubuntu for information leading to a solution.

TIA,

Snod[/QUOTE]

Deactivate the wireless, then deactivate the wired. Then activate the wireless. If it takes more than 40 secs to activate.....its not working come back here.

---

