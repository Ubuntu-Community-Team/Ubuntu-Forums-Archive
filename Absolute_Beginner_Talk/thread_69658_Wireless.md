---
title: "Wireless"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by ProPilot on 2005-09-27
Breezy system D-Link DWL-G650 in a HP Pavilion ze5170 wireless worked basical right out of the box, however, under System-Administration-Network then properties for the wireless connection the WEP input box only allows 25 characters and yet I need to input 26 characters. How do I do this?

Thanks
Tom

---

### Post by mlomker on 2005-09-27
I assume that information is placed in the /etc/network/interfaces file.  You could try editing it directly.

---

### Post by ProPilot on 2005-09-27
That's where my being a nOOb comes in. How?

Thanks
Tom

---

### Post by mlomker on 2005-09-27
**gksudo gedit** from a terminal and then open the file.

---

### Post by ProPilot on 2005-09-27
Sorry my fault
I know about gedit but once i have the file open what do i write into it?

Thanks
Tom

---

### Post by Comrade on 2005-09-27
Stuff like this:
iface eth0 inet dhcp
wireless_essid WHATEVER
wireless_mode Managed
    wireless_channel WHATEVER
wireless_key WHATEVER

You will need to find out the following information for your network:
ESSID, Mode, Channel, and WEP Key. Also, you may be using wlan0 instead of eth0, in which case you would have to change accordingly.

---

### Post by ProPilot on 2005-09-28
OK great. Thanks very much. I will proceed with your input.

Tom

---

