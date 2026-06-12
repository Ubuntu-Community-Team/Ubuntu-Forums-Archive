---
title: "Problem with drivers in Edgy"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by silentsoul on 2007-02-02
I am fairly new to Linux and I have been googleing and RTFMing for the last 2  days. The problem I am having is that  I have a Toshiba Sat A135 with An atheros chipset ar5006eg, I got the computer to recognize the card once and load up, but after about 15 minutes it stopped working.After trying multiple mad wifi drivers and reading every forum I can find no one tells how they fixed the problem or the solutions don't work. This is what I can give you.
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
computer@:~$ 

computer@:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

2.6.17-10-generic
Thanks for your help.

---

### Post by silentsoul on 2007-02-02
Just wanted to give a little bump, I've tried using the repositories and a clean install with no luck, Dapper does not support the 5006EG card either, madwifi says the next release will fix the problem but who knows when that will be, any help would be greatly appreciated.

---

### Post by orb9220 on 2007-02-02
open your /etc/network/interfaces file and copy and paste here.

In Term : gedit /etc/network/interfaces

Did you or are using the network-manager applet?

If you installed it it will stop the wireless working until you insert a # comment symbol in front of all the entries except the Auto Lo at the top


Here is what I did to get wireless working again.

in a term : gksudo gedit /etc/network/interfaces 
and put comment symbols like below.


> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


save and reboot, Hope that helps.

---

### Post by silentsoul on 2007-02-03
I am using the networking tool in the system admin drop down menu. Should I add these comment symbols on a fresh install of edgy? Because I know it installs the restricted modules automatically. Edit: I added comments to all the lines and still no wifi. Any other ideas, I'm gonna try to kill all the madwifi modules and install a differnt madwifi version and re configure the ath0. any ideas on this?

---

### Post by silentsoul on 2007-02-03
Just wanted to throw this out there might help a little.

computer@(none):~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


computer@(none):~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

computer@(none):~$ wlanconfig ath0
bash: wlanconfig: command not found

---

### Post by Lonthong on 2007-02-05
Try to use madwifi-ng driver r1711 or later.
See my post in this [thread]("http://ubuntuforums.org/showthread.php?t=212600&highlight=atheros+ar5006eg") for more details.

---

