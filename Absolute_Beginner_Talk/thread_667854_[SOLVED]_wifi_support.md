---
title: "[SOLVED] wifi support"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by jatiesch on 2008-01-14
hi i could not enable my wifi connection....
i have AMD64 machine and gusty installed with a Netgear WG311v3 network card..

For ur support here is terminal output:

[I]jatiesch@jatiesch-desktop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
jatiesch@jatiesch-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[/I]

plz guide how to proceed so that i can run internet and use ubuntu to full potential
Thanks in advance...

---

### Post by angryfirelord on 2008-01-15
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")
(The version numbers are newer, but the installation process should be the same)

---

### Post by jatiesch on 2008-01-15
hi thanks...
 i went through the guide mentioned by u but there following is written:

"*You can get ndiswrapper for amd64, but I don't think there are actually any 64-bit drivers for this hardware even in Windows-land. That may change in the future, but for right now if you're running a 64-bit environment, you're probably out of luck.*"

i have AMD64 processor....how to proceed???

---

### Post by jatiesch on 2008-01-15
anyone??

---

### Post by jatiesch on 2008-01-18
bing!!!
has no one faced such problem??

---

### Post by jatiesch on 2008-01-18
#4   Report Post  
Unread 1 Minute Ago
jatiesch jatiesch is online now
5 Cups of Ubuntu
	  	
Join Date: Aug 2007
Location: India
Beans: 23
Ubuntu 7.10 Gutsy Gibbon User
Windows User
Thanks: 0
Thanked 0 Times in 0 Posts
Unhappy Re: wifi support
After going through given guide i got this....

jatiesch@jatiesch-desktop:~$ lspci | grep Marvell
01:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

jatiesch@jatiesch-desktop:~$ ndiswrapper -h
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile install driver described by 'inffile'
-a devid driver use installed 'driver' for 'devid' (dangerous)
-r driver remove 'driver'
-l list installed drivers
-m write configuration for modprobe
-ma write module alias configuration for all devices
-mi write module install configuration for all devices
-v report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

jatiesch@jatiesch-desktop:~/CB-35P_3_1_1_7_Release/Inf/WinXP_2K$ ls
mrv8335.cat mrv8335.inf MRV8335NT.sys MRV8335XP.sys
jatiesch@jatiesch-desktop:~/CB-35P_3_1_1_7_Release/Inf/WinXP_2K$ sudo ndiswrapper -i mrv8335.inf
installing mrv8335 ...

jatiesch@jatiesch-desktop:~$ ndiswrapper -l
mrv8335 : driver installed
device (11AB:1FAA) present
jatiesch@jatiesch-desktop:~$ sudo modprobe ndiswrapper
jatiesch@jatiesch-desktop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.



so the problem continues..
plz help...

---

