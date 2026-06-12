---
title: "No add button in Networking Confiuration tool"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by 3booter on 2005-12-27
I've gone from dial up to wireless DSL connection. Wireless works perfectly with XP. Ubuntu 5.10 Device Manager shows the new wireless PCMCIA card. When I open the Networking Configuration Tool, there is no add button. I'm at a loss as to how to procede in setting up the wireless conection. I LOVE UBUNTU! Any problems I've had setting up and configuring have been easily solved, as I'm sure this one will be. Very much looking forward to dumping XP on this laptop. Thanks for any help.
5.10 installation is upgrade from beta.
Dell Latitude PIII 650
Dual boot XP/Ubuntu
Linksys wireless G notebook adapter with speedboost
dialup no longer available

---

### Post by rancourt on 2005-12-27
Hey there. This problem's a bit advanced for me, but I think I have a little insight into what might be happening which may prove useful in a small way to you. If this proves unhelpful, please accept my apologies in advance. 

Ubuntu's network tool is a configuration manager, not a hardware manager -- the fact that your wireless card isn't showing up in it suggests that Ubuntu doesn't realize it has a wireless card, specifically, attached. The entry in the device manager simply shows that Ubuntu realizes it has a hardware device of that name attached to its PCMCIA bus. In Windows, this would be similar to an exclamation point next to the icon in Device Manager -- it sees the hardware, but it doesn't necessarily have a working driver configured for it.

Unfortunately, here's where I run out of steam mentally -- I don't know much at all about probing for hardware drivers, aside from the fact that it involves the modprobe command. One "total clueless" possibility I'd offer might be to boot a LiveCD, see if it recognizes your wireless NIC, and read the system log to see what driver it chose for it.

I hope this helps a little, and mostly help someone much more knowledgable than I can help further.

---

### Post by amohanty on 2005-12-27
Take a look at this wiki page:
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards)

HTH
AM

---

### Post by 3booter on 2005-12-27
Thanks for the Windows analogy. Forest for the trees! Good idea also on the live CD, but on this creaky little laptop, a new install (which I'm not ruling out) would be faster. Anyway, thanks for re-directing my thoughts. I'm sure I'll come up with the right drivers in no time.

---

### Post by 3booter on 2005-12-27
Thanks! The page looks like a great spring board.

---

### Post by tokyovigilante on 2005-12-27
Hi,

Try posting the results of the following terminal commands:

lspci
iwconfig
ifconfig

What model PC card wireless card are you using? Do you know if it is compatible with Linux?

---

