---
title: "network settings"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by seltzer on 2007-03-01
I just got a used laptop (c. 2001) with ubuntu Linux installed.
I'd like to connect it to the Internet for Web browsing, but unlike with my Windows systems, this one does not automatically take care of the network settings.
My ISP (RCN, cable modem) does not support Linux; and won't answer any Linux-related questions.
I have a static IP address. I've entered that.
I don't know what else to enter and where.
Please help.

Thank you.

Richard Seltzer, [email]seltzer@samizdat.com[/email], 617-469-2269

---

### Post by BillGod on 2007-03-01
easiest way is to enter in your info under system\administration\network

Click on your wired connection and hit properties.  set you static ip, netmask and gateway.  your isp will have to provide all that info for you,  you will also have to click on dns and add your dns servers.  again your isp will provide that.

To test if you have it setup right.  open a terminal window and ping google.com.  If you get a response your good.  If you get an unknown host error.  ping your gateway.  if you get that far your ip, netmask and gateway are good.  then check dns.

---

