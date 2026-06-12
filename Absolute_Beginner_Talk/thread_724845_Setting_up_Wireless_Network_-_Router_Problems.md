---
title: "Setting up Wireless Network - Router Problems"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by LCollins on 2008-03-15
I'm a Linux newbie, and I'm trying to set up a wireless network but run into problems in trying to connect to the router. I'm using Ubuntu 7.10, and my wireless card is a Netgear WG511v2 (Made in China). I have successfully installed the Windows driver using ndiswrapper (or so I think as the lights are on and network manager recognises that some wireless networks exist).

I have been following the troubleshooting instructions and got up to the 'Connecting to the Router' part, where I have followed the instruction to type in iwconfig. I have got back ESSID=off/any. I'm a little lost from here on, also with another instruction to 'reboot the kernel'. wpasupplicant has been installed. Could anyone please help me with steps here on in to complete connection to a wireless network.

Thankyou
LCollins

---

### Post by dstew on 2008-03-15
What is your router set-up? That is, what is the ESSID, encryption settings, and is it enabled as a DHCP server? You should be able to check and change these settings on your router by using a cable connection to it.

You should be able to set up your wireless card settings in the System --> Administration --> Networking panel without using iwconfig.

---

### Post by LCollins on 2008-03-15
The ESSID is currently set to 'off/any' and I cannot seem to change it. The encryption is WPA 1 but this should not be an issue as I have wpasupplicant installed. The router is enabled as DHCP, but I am currently using a static IP on my laptop, for the sake of simplifying the issue. I've tried the Network Manager, but have read (on the internet) that it can be a bit buggy/unreliable, so to conquer that I've been trying to fix this through Terminal.

Thanks for your help,
LCollins

---

### Post by dstew on 2008-03-15
> The ESSID is currently set to 'off/any' and I cannot seem to change itThis is the setting on your router?

---

### Post by LCollins on 2008-03-15
No, this is the setting on my computer. The layout of the wireless network is such: There is a router which is also the gateway to the internet. On this network is two other computers (which use Windows XP and are having no issues). Then there is my computer which I am trying to connect to the router. It is this computer, which despite having a working wireless card, will not even ping the router, though it does recognise that the wireless network exists, as the router is listed as an access point.

Thanks for your help so far,
LCollins

---

### Post by LCollins on 2008-03-15
Thankyou for your help dstew, but I have now solved the problem. There was MAC filtering in place on the router, so it was a simple matter of safe listing my MAC address.
Many thanks,
LCollins

---

