---
title: "Can't Connect to Internet"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by RinSess on 2006-09-16
I've just installed Ubuntu on my 250GB hard drive(I’ve done nothing else in Ubuntu) but can't connect to the internet(ADSL), which I was using without issues on Windows XP.

My specs are:
Modem - iConnectAccess621, ethernet connection
Processor - Intel Pentium D Dual Core 3GHz
Graphics Card - ATI Radeon X600
Hard Drive - Western Digital JS 250GB SATA
           - Western Digital SD 320GB SATA 
Memory - NECC Dual Channel DDR2 533 MHz SDRAM 1GB

Ubuntu is on the same hard drive as Windows XP

I've checked the Ubuntu documentation and opened up a terminal typing in the following command:

"sudo pppoeconf"

The ethernet card was detected. However, the following message appeared:

"Sorry, I scanned 1 interfact, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem"

I then tried to do a manual connection using "sudo pon dsl-provider" but funny characters kept appearing every few seconds and I had to shutdown the terminal.

So, how do I connect to the internet? Should I have shut off my modem when starting Ubuntu? What is the access concentrator? What's the other pppoe process? 

By the way, I can't open my drives in "Computer", it looks like I have to set up permissions.

Please help. Thanks in advance.

---

### Post by xmastree on 2006-09-16
You should be able to set it up from System>administration>Networking in the menu.

[ATTACH]15822[/ATTACH]

Make sure eth0 is set as the default interface and that it's set to DHCP. activate it, and that should be all you need.

As for your drives, I presume you mean the windows ones? You need to mount them first.

See here:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

### Post by RinSess on 2006-09-16
I checked the Network Settings, and the default was already eth0 and set to DHCP.

---

### Post by spur on 2006-09-16
If you have a direct connection then you should have 'coonect to the internet directly' with an x in it in system settings -> connections->proxy and in system settings -> network settings -> network interfaces you should have etho with an ip address(you dont put it in) and protocol dhcp and active with a green tick and commnent 'ethernet network device'.
This presumes etho 0 is the one you have connected to your router/modem and you have a direct connection and you are using kubuntu. ubuntu would have the same settings but got at differently. If you have more than one eth card you could be using the wrong one. If you are in doubt that you are using a direct connection ask your provider.
If you are using dial up ignore what I have said as it doesn't apply.

---

### Post by RinSess on 2006-09-16
The Network Proxy and Network Settings are already correctly set up to connect to the internet directly and using the ethernet device. What else should I do?

---

### Post by spur on 2006-09-16
I know some would grimace but try a reboot. It should be working as is. Are you sure your connection is a direct connection and no proxy is needed also turn off your firewall as that sometimes causes probs.

---

### Post by RinSess on 2006-09-16
I reboot every time I come onto these forums, as I have Windows XP on the same computer.

In relation to the proxy, what does it mean and how do I know what option I'm supposed to choose.

I do not have a firewall in Ubuntu.

---

### Post by spur on 2006-09-16
When you connect to the internet with xp do you go thru a proxy?
If not and you are using a direct connection then check sytem settings -> connections-> proxy  'connect to the internet directly' needs a x in its box.
If you are using a proxy your ISP will be able to tell you or take a look at your xp settings. I can't tell you what those settings should be if you need to set them.

---

### Post by RinSess on 2006-09-17
I do not go through a proxy on Windows XP. The direct internet connection has been chosen and it still doesn't work.

---

### Post by spur on 2006-09-17
Good then is your proxy setting as mentioned in my previuos post? If it is you have something getting in the way, like maybe an attempt to connect thru another program in the past has stuffed something up. You may have to check if one of them is not trying to connect and stop it. Sorry I am not familair with the dial up programs and how they work to help you with that.

---

