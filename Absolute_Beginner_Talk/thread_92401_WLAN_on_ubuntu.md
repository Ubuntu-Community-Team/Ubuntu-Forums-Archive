---
title: "WLAN on ubuntu"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by S1RHC on 2005-11-19
Can someone describe the procedure I have to follow in order to connect to a WEP protected WLAN using a USB NetGear WG111? :)  I googled it allready but no decent answers :(
thanx a lot for your help :)

---

### Post by danne on 2005-11-19
[QUOTE=S1RHC]Can someone describe the procedure I have to follow in order to connect to a WEP protected WLAN using a USB NetGear WG111? :)  I googled it allready but no decent answers :(
thanx a lot for your help :)[/QUOTE]
have you already installed the drivers correctly?

if not: install ndisgtk and load the .inf file of the windows driver of your card.

if so: go to your network connections and choose the ESSID...when you click on it, it prompts for your WEP-key

...if you mean you want to log in to another wlan try using airsnort

bye

---

### Post by S1RHC on 2005-11-19
Well, I haven't installed Ubuntu yet, I ask if I will be able to connect to my WLAN prior to dloading because I am on a slow DSL line and I can't download a useless (for me if it doesn't connect to the WLAN, not for anyone else) 700mb distro. I 've got to ask :)
I want a " Yea, there is certainly a way to connect to your WLAN for me to start dloading, and then I'd like to have someone to tell me a exactly what to do, coz I'm a linux virgin... And if I don't have WLAN I won't have internet, so I won't be able to connect and ask you what to do... ;)

---

### Post by shade87 on 2005-11-21
I have problems in configuring Wlan with Netgear WG 111 (S/N: WG72). I have to use WEP encryption.
First of all I installes ndiswrapper and ndisgtk. I download driver from netgear.com
ndisgtk shows that hardware is present, light ist blinking.
a scan with iwconfig shows the right ESSID.
Everythime I want to configure my network with ndisgtk the console displays the following error: While connecting to session manager:
Authentication rejected, reason: None of the authentication protocols specified are supported and host-based authentication failed.

Result of ifconfig:
wlan0     IEEE 802.11b  ESSID:"hoehenweg"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:90:4B:1C:C5:25 
          Bit Rate:11 Mb/s   Tx-Power:32 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Encryption key:my key   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-50 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:328   Missed beacon:0


/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp
iface wlan0 inet dhcp
wireless-essid hoehenweg
wireless-mode managed
wireless-key s:1234567890123 (for 128-bit encryption)
auto wlan0
auto eth0

Can anyone help me?

---

### Post by danne on 2005-11-21
[QUOTE=S1RHC]Well, I haven't installed Ubuntu yet, I ask if I will be able to connect to my WLAN prior to dloading because I am on a slow DSL line and I can't download a useless (for me if it doesn't connect to the WLAN, not for anyone else) 700mb distro. I 've got to ask :)
I want a " Yea, there is certainly a way to connect to your WLAN for me to start dloading, and then I'd like to have someone to tell me a exactly what to do, coz I'm a linux virgin... And if I don't have WLAN I won't have internet, so I won't be able to connect and ask you what to do... ;)[/QUOTE]

well if you do it like I've said, everything should work like a charm

---

### Post by janne5011 on 2005-11-21
hi I think something like this possible works but I dont really understand why you have one "etho0" .remove?

anyway here is suggestion for /etc/network/interfaces

# The primary network interface

iwconfig wlan0 essid 'hoehenweg' mode Managed key restricted 1234567890123
dhcpcd wlan0
auto wlan0

hope this works for you:)

reboot!

---

### Post by danne on 2005-11-21
right...I was about to answer..lol
nvm

---

