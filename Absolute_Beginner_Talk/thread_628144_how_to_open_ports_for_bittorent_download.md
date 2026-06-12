---
title: "how to open ports for bittorent download"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by kahram.yoon on 2007-11-30
how do you open ports for bittorent download?  I typed "sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT" into terminal and it should have opened the port but when i go test it using deluge's ip test in the preferences, it says that port is not opened.

---

### Post by mellowd on 2007-11-30
Are you sure the port is open on your router/firewall?

---

### Post by kahram.yoon on 2007-11-30
i dont have any firewalls or antivirus programs and stuff like that.

---

### Post by mellowd on 2007-11-30
I'm talking about hardware. How do you connect to the internet

---

### Post by kahram.yoon on 2007-11-30
my computer internet cord is connected to my phone adapter (linksys spa2102-r) and the phone adapter cord is connected to my broadband modem.

---

### Post by mellowd on 2007-11-30
The linksys spa2102-r is yoru router. You'll need to setup port forwarding on it. 

Have a look here: [http://www.portforward.com/](http://www.portforward.com/)

---

### Post by mellowd on 2007-11-30
[http://www.portforward.com/english/routers/port_forwarding/Linksys/SPA-2102/SPA-2102index.htm](http://www.portforward.com/english/routers/port_forwarding/Linksys/SPA-2102/SPA-2102index.htm)

Select the program you are trying to do it for

---

### Post by kahram.yoon on 2007-12-01
how do i get my static ip address? i need it in order to open ports using the website you have given me.

---

### Post by mellowd on 2007-12-01
> **kahram.yoon said:**
> how do i get my static ip address? i need it in order to open ports using the website you have given me.

You will need to configure a static IP address for your PC to get from the router. I can't tell you how as there are thousands of different routers and they all do it slightly differently. You will need to check the manual.

---

