---
title: "Upgraded to Fiesty - Wireless Connection Down"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by tl3000 on 2007-04-20
Upgraded from a working Edgy Ubuntu setup to Fiesty...  The wireless connection no longer works now.  The setup is a Compaq M700 laptop with a Netgear WG511v1 pcmcia card connecting to a 802.11g network using WPA-PSK.  The original wireless connection with Edgy was accomplished with NDISWRAPPER using the Windows Netgear driver (netwg511.inf).

After upgrade to Fiesty, I tried to re-establish the wireless connection using the same Edgy setup but I was unsuccessful.  The adapter powers up much earlier in the Fiesty boot up process than Edgy--even before user log in, and the Activity LED flashes very rapidly indicating a lot of attempts at network traffic.  I also tried to re-enter the WPA-PSK passphrase but the Network Manager does not provide the WPA options anymore just WEP.  The Network Manager did manage to recognize and list my network showing its SSID among others but the signal strengths for all the found networks are much lower than normal--even when I placed the laptop next to the router.  I blacklisted 'prism54pci' in /etc/modprobe.d/blacklist and the abnormal Activities LED rapid flashing went away, the signal strength indications also seem to be back to normal, and the WPA options reappeared in the Network Manager.  Re-entered the WPA-PSK passphrase, and I was able to re-establish intermittent wireless connection once.  The connection would be up for just a few seconds, goes down again, and attempts to re-connect but defaults to connecting with a neighbor's unsecured network.

Any ideas would be appreciated...

---

### Post by M-Z on 2007-04-20
I have almost the same problem. When using bcm43xx driver I can connect to Internet for a short period of time, after which my connection breaks (although network manager still claims I'm connected). When using ndiswrapper I cannot connect altogether.
It seems to be a problem with WPA, because when I turned off security settings in router's configuration, I was able to connect to the network.
My hardware is Acer 3003LMi - internal WLAN card Broadcom 4318 rev 2, my router is Linksys WRT54G, security setting - WPA Personal, TKIP.

---

### Post by tl3000 on 2007-04-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105858](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105858) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I was able to get my wireless connection to work again with this temporary solution.  See related bug report... FYI.

---

### Post by jbonll05 on 2007-04-28
HP/Compaq NX6110, BCM4318,Belkin G+ router cofigures by disabling security features. Am using it now on my local network. Machines runs fine with ndsiwrapper on another hd I swap.
JB,Ubuntu user since 40ct05

---

### Post by tl3000 on 2007-04-28
That's not 'working' for networks requiring WEP/WPA...

---

### Post by tl3000 on 2007-05-04
RESOLVED - [my resolution]("http://ubuntuforums.org/showpost.php?p=2585938&postcount=19").

---

