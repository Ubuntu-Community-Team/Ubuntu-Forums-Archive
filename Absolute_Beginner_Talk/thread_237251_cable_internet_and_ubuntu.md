---
title: "cable internet and ubuntu"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by jmax on 2006-08-15
I am having great troubles getting Ubuntu 6.6 to talk to the net via the telstra {australia} bigpond cable. The o/s knows the modem is there, the connection is apparently good but it simply won't talk to the net ... much like any other linux disto alas. I would like to try ubuntu but this seems to be a bit of a problem. How does one step by step {being a newbie to linux} get ubuntu to use a cable internet connection? 

I've tried for quite some time and had to reinstall XP so I could use the net. Would like to be M$ free but this is a bit of a silly stumbling block. 

John

---

### Post by deadgobby on 2006-08-15
That is strange. Cause Ubie should dectect the signal coming in from the cable modem. A simple task it to shut down the modem. Like unplug and replug it in after a minute. Let the modem self test and leave the modem on. Reboot Ubie and see if it finds it and click on the icon. If you install Ubie it had to check for connection. Yet, when you reinstall Ubie. Leave your cable modem on too.
 
 If no connection go to System>admin>network settings. Check to see if the settings are on DHCP in the properties on the either card. Check DNS  tab and see if it calls up DNS servers.

---

### Post by goatflyer on 2006-08-15
Perhaps your ISP is using pppoe.  If you have your isp userid and password, you could open a terminal and type pppoeconf

---

