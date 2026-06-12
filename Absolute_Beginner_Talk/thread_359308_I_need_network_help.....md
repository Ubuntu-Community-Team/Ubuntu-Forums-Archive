---
title: "I need network help...."
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by New-buntu on 2007-02-11
Yay, my network card works.... now what (it doesn't detect the network, running edgy....)

---

### Post by nickoli_02 on 2007-02-11
We're going to need much more information than that about your network setup in order to help you. Are you behind a router? Are you on a cable/dsl line? Is this a wireless or wired connection you're having troubles with?

---

### Post by New-buntu on 2007-02-11
Oh, yeah.. sorry... duh...ok I'm using verizon fios, I finally got NDISWrapper to see my Belkin F5D6050 IEEE wireless b USB network card and I have a router/modem that's wireless that connects directly to the internet....

---

### Post by Zuuswa on 2007-02-11
try downloading and using wifi radar.  It will list the available wireless networks in range and let you choose one to connect to.

---

### Post by nickoli_02 on 2007-02-11
What is the security like on your wireless network? Ubuntu does not natively support WPA, you'll need to use WEP encryption if you want your network to be protected (generally a good idea). To connect to the network, you need to configure the network interface in System -> Administration -> Networking. Select the wireless interface and click Properties. There you can enter your SSID and WEP password, configure the static IP or use DHCP. 

If you want to use WPA you'll need to configure wpa_supplicant. Do a search of the forums for a howto :)

---

### Post by New-buntu on 2007-02-11
Ok, gonna give it a shot

---

### Post by New-buntu on 2007-02-11
ok, so now I can see the wireless router/modem... but it's having trouble acquiring the IP address... It can connect but it can't obtain that IP address. I've tried playing around with the settings and stuff. it's not working, How do I make it get that IP address?

---

### Post by nickoli_02 on 2007-02-12
Is your router set to DHCP or static IP? If it's static you'll need to tell both the router and your computer what IP to use. If it's using DHCP and it's not working then try using a static IP and see if that works.

---

