---
title: "Port Forwarding"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-08-21
How can I forward a port in Linux?  I need to do it to configure Azureus properly.

Thanks for your help.

---

### Post by cwaldbieser on 2005-08-22
[QUOTE=apmcavoy]How can I forward a port in Linux?  I need to do it to configure Azureus properly.

Thanks for your help.[/QUOTE]
If you mean that you want to send traffic from address1:port X to address2:port Y in a transparent manner, there are a couple ways to accomplish that.  I have a spiffy python program I got from the ActiveState site called "pinhole.py" that does exactly that: [http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/114642](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/114642)

There are probably also ways to do this with iptables or maybe ssh port forwarding.

Feel free to ask if you require further details.

---

### Post by bored2k on 2005-08-22
[QUOTE=apmcavoy]How can I forward a port in Linux?  I need to do it to configure Azureus properly.

Thanks for your help.[/QUOTE]
 [http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm)

Look your router up, follow the guide. Easy as cake. Azureus usually requires port 6881 for downloading and utilizing the DHT tracker (even if you change the port, the default DHT port is still 6881 unless told otherwise).

---

