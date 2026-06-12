---
title: "How do I permanently change the MAC address ?"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by madalin on 2006-06-21
My internet service provider bind their services to a specific MAC address. I changed my network card and every time I am rebooting I have to change the original MAC address of my Network Interface Card. 

I know how to do this from console using ifconfig ... but I want to change the MAC address **Permanently**. 

How can I do this ? Maybe I can place the commands in a runtime control script or modify some configuration files ? Where is the Ethernet configuration file for interface eth0 ? I couldn't find the ifcfg-eth0 configuration file in /etc :confused: 

Please help me !

I am in love with Ubuntu :mrgreen:

---

### Post by steve.horsley on 2006-06-21
the config file is **/etc/network/interfaces**. **man interface**s will get you loads on info on this. 

Basically, I think you need to find the line like:
**iface eth0 inet dhcp**
 and add a line afterwards like:
**up ifconfig eth0 blah blah**

This would change the MAC as the interface is brought up. 

HTH

---

### Post by madalin on 2006-06-21
Thank you steve.horsley !

First I have tried to change the line afterwards "iface eth0 inet dhcp" like you said
(up ifconfig eth0 blah blah).  But this is not working (at least not for my network card).

So I started to read man interfaces ...  and I founded the pre-up command (run command before bringing the interface up). Now it's working. :D 

**[COLOR="DarkRed"]So the solution for the problem was:[/COLOR]**

[B]- open a terminal

- enter the following command in order to edit the /etc/network/interfaces configuration file :
sudo gedit /etc/network/interfaces

- you will be asked for your password

- when the file is opened in gedit editor you need to find the line like this (if your network card is eth0):
iface eth0 inet dhcp

- add a line afterwards like (replace 00:00:00:00:00:00 with your MAC address): 
pre-up ifconfig eth0 hw ether 00:00:00:00:00:00

- save the file and reboot[/B]

That's all folks!
Once again thanks to you steve.horsley

---

### Post by steve.horsley on 2006-06-21
You're welcome. I didn't know you'd need pre-up. Glad you got it fixed.

---

