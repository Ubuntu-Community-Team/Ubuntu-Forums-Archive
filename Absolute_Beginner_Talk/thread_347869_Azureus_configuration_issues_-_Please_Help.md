---
title: "Azureus configuration issues - Please Help"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Faisalahmad on 2007-01-27
Hi I am a new linux/Ubuntu user.  Just migrated from the XP environment.

I have installed Azureus from the Applications menu software upload/download option.  During the first run the program started to configure itself.  At the port test step it gave a message TCP 6880 port is used for some internal application and tested port 28481 but keeps giving me a NAT test failure.

One of the messages suggested I allow the UDP port 28481 in my filewall/router.  I have a D-link DI524 router.

How can I configure Ubuntu firewall (if it a software controlled one) or the router firewall to allow this port?

Also is there something I need to do in Ubuntu or Azureus configuration to make the software work for me?

Please help

---

### Post by riven0 on 2007-01-27
You'll have to do two things. First, configure you D-Link router to accept Azureus. So, open firefox, type **192.168.0.1**, log in, go to the Advanced menu and add in Azureus with the ports you want open. You can include both the TCP and UDP ports.

Then, open the terminal, and open the ports through there:

> sudo iptables -A INPUT -p tcp --dport 28481 -j ACCEPT

Do the same for the UDP port.

Now try restarting and see if it works. If not, try installing **firestarter **and open the ports through there.

---

### Post by Faisalahmad on 2007-01-30
Thank you.  I will try this today and post an update.

---

