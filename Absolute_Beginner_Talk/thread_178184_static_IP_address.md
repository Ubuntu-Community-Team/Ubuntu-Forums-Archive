---
title: "static IP address"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by Trosky on 2006-05-17
Hello, I installed a belkin card through ndiswrapper. The router is working with "static IP address" (no DHCP). But the problem is that I cann´t save the  configuration when I activate "static IP address", it just deactivate the confirm button.

$  ndiswrapper -l
Installed ndis drivers:
rt2500          driver present, hardware present
linux@linux-laptop:~$

$ tail /var/log/messages
May 17 15:49:13 localhost syslogd 1.4.1#17ubuntu7: restart.

---

### Post by steve.horsley on 2006-05-17
First, I don't think you need ndiswrapper for an rt2500 card. Not on Dapper, anyway - it's supported out of the box. But if you have ndiswrapper working, no worries then.

When you select static IP address, you also need to supply more information (the three empty fields below for starters). You need to specify the IP address of the PC, the subnet mask (255.255.255.0 is a good guess if you don't know that one), and the default gateway (meaning the IP address of your router). 

You will also have to provide the IP address of at least one DNS server.

---

