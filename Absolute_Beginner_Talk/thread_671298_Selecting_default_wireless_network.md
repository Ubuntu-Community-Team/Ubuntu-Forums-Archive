---
title: "Selecting default wireless network"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by ladybumavere on 2008-01-18
Every time I boot into Ubuntu it starts connecting to another wireless network in my area instead of my own.  How can I tell Ubuntu to only connect to mine?

---

### Post by smurphy_it on 2008-01-18
You could try putting your router config info in the /etc/network/interfaces file.

Below is an example

auto eth1
iface eth1 inet dhcp
wireless-essid 'name'
wireless-key 1234567890
gateway 192.168.0.1

If your wireless card is not ETH1, then change it to it's proper name (like eth3, ath0, wlan0, etc).
Then change the wireless-essid to the name of your router's essid and of course change the wireless-key and gateway if it isn't 192.168.0.1

This way should work for WEP encrypted networks.  WPA would be setup differently.

---

### Post by ladybumavere on 2008-01-18
> **smurphy_it said:**
> You could try putting your router config info in the /etc/network/interfaces file.

Below is an example

auto eth1
iface eth1 inet dhcp
wireless-essid 'name'
wireless-key 1234567890
gateway 192.168.0.1

If your wireless card is not ETH1, then change it to it's proper name (like eth3, ath0, wlan0, etc).
Then change the wireless-essid to the name of your router's essid and of course change the wireless-key and gateway if it isn't 192.168.0.1

This way should work for WEP encrypted networks.  WPA would be setup differently.


Honestly, I don't even know how to find out what my wireless card is named or how to do any of that! :oops:
I just started using Ubuntu and Linux in general, so I don't know anything yet.
Could you step me through it or link me to a thread that has a general step by step?

---

### Post by ladybumavere on 2008-01-19
No other help available?


:( :( :( :( :( :( :( :(

---

### Post by SmileyChris on 2008-01-19
Try this:

Left click on the wireless icon in the notification area, select "Manual configuration..."

Click on "Wireless connection" then click the "Properties" button

Uncheck "Enable roaming mode" then fill in your wireless details.

---

### Post by avik on 2008-01-19
I've been looking for answers to the same problem.  Is there a way to enable roaming mode (for when I'm not at home), while still setting which network I would *prefer* to use if available?

---

### Post by ladybumavere on 2008-01-19
> **avik said:**
> I've been looking for answers to the same problem.  Is there a way to enable roaming mode (for when I'm not at home), while still setting which network I would *prefer* to use if available?



That's exactly what I want.

WE MUST FIND THIS ANSWER!

---

### Post by ladybumavere on 2008-01-21
Nobody has any answers?

---

### Post by smurphy_it on 2008-01-22
Well first of all, does your wireless work.  If the answer is yes, you can just follow the steps which SmileyChris said.

Just click on System, Administration, Network.  Then click wireless and choose properties, then uncheck "Enable roaming Mode".  After that just enter your information for your wireless connection.  ESSID, pasword type (wep/wpa) and the password.  If your router is setup as a DHCP server it will automatically assign you an IP address, so under the connection settings, configuration you can just select DHCP.

These steps are assuming that you are running Ubuntu, and not another one like kubuntu, edubuntu, etc... as they have different network managers, so the steps can be different.


If your wireless is not working, then I'd suggest start by trying the Restricted drivers.  Click System, Administration, Restricted drivers manager.  Click the wireless and Enable it.  It is best to have a wired network connection here as it will want to connect to the internet to download the drivers for your wireless card.

---

### Post by ladybumavere on 2008-01-22
> **smurphy_it said:**
> Well first of all, does your wireless work.  If the answer is yes, you can just follow the steps which SmileyChris said.

Just click on System, Administration, Network.  Then click wireless and choose properties, then uncheck "Enable roaming Mode".  After that just enter your information for your wireless connection.  ESSID, pasword type (wep/wpa) and the password.  If your router is setup as a DHCP server it will automatically assign you an IP address, so under the connection settings, configuration you can just select DHCP.

These steps are assuming that you are running Ubuntu, and not another one like kubuntu, edubuntu, etc... as they have different network managers, so the steps can be different.


If your wireless is not working, then I'd suggest start by trying the Restricted drivers.  Click System, Administration, Restricted drivers manager.  Click the wireless and Enable it.  It is best to have a wired network connection here as it will want to connect to the internet to download the drivers for your wireless card.



My wireless is working perfectly fine, but this is what I'm looking for...

> **avik said:**
> I've been looking for answers to the same problem.  Is there a way to enable roaming mode (for when I'm not at home), while still setting which network I would *prefer* to use if available?

---

### Post by rosegarden78 on 2008-01-22
If you don't have those wireless bars in your system dock you need to press Alt-F2 or type in  a terminal: **nm-applet**.  I just select a network from the dock icon and it remembers next time. And yes check settings - network to make sure **roaming mode** is enabled.

---

### Post by ladybumavere on 2008-01-22
Now I've got a new problem.  For some reason I cannot connect to my own wireless network anymore.  No idea why.  Usually when I select a network to connect to the bottom dot will turn green then the top will turn green then it shows the bars.  Which I select my wireless network now, the bottom bar never turns green; it just sits there and spins endlessly.

Any guesses?


I'm using a Linksys PCI WMP54G.

---

### Post by ladybumavere on 2008-01-22
> **ladybumavere said:**
> Now I've got a new problem.  For some reason I cannot connect to my own wireless network anymore.  No idea why.  Usually when I select a network to connect to the bottom dot will turn green then the top will turn green then it shows the bars.  Which I select my wireless network now, the bottom bar never turns green; it just sits there and spins endlessly.

Any guesses?


I'm using a Linksys PCI WMP54G.


And now it's worsened and I cannot even see my wireless network.

---

### Post by rosegarden78 on 2008-01-22
My network drops sometimes I unplug the power on the router and modem and plug it back in.  If it was previously detected and it just disappeared that could be it.  It sounds like your wireless card is working so that's good you didn't have to use modprobe bcm43xx.  Other than that are you within range?  I use a Linksys WRT54G and range is limited to three or four rooms or 20 meters.  Can you get online with Ethernet cable instead of wireless?

---

