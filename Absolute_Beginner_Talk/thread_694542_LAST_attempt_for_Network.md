---
title: "LAST attempt for Network"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by ThePinkWitch on 2008-02-12
I have spent hours on this so one last time. I have a ADSL Broadband internet with a wireless modem. In my main computer (running WinXP) I have a Net gear WG311v3 wireless PCI adapter. In my second computer I have a Netgear  WG111v2 USB Adapter (dongle) running with Ubuntu 7.10. Previously the main computer was set up to another computer via a network and that computer is no longer here. The problem for me is that someone else set up the network and I'm not sure what the settings are. Now I have a different computer and have installed Ubuntu on it. I have tried using Ndiswrapper but after messing around blacklisting drivers and uninstalling Ubuntu and trying WiFi Radar and Wcid whatever, I realise that the dongle works out of the box anyway and I still can't get the network to work for more than a few minutes. Ther is a list of stuff comes up in avaliable networks so I guess some are the neighbours. What I need is someone to go thru with me what is on the main comp ans see if I have the settings right for the second one. Phew!! that was long winded. It's hard because I knew nothing about this stuff when I started trying to get it to work. Thanks to anyone who might want to help :)

---

### Post by ThePinkWitch on 2008-02-12
I guess it's time to give up ](*,)

---

### Post by Pelham123 on 2008-02-12
> **ThePinkWitch said:**
> Now I have a different computer and have installed Ubuntu on it. 

With the WG111 v2 Dongle?

> **ThePinkWitch said:**
> I have tried using Ndiswrapper but after messing around blacklisting drivers and uninstalling Ubuntu and trying WiFi Radar and Wcid whatever, 

Ina terminal, type in the following commands individually and paste output into reply:

lsusb
ndiswrapper -l
iwconfig


> **ThePinkWitch said:**
> I realise that the dongle works out of the box anyway and I still can't get the network to work for more than a few minutes.

Does this mean you have *some* internet access, ie - you can browse the web?

---

### Post by dstew on 2008-02-12
> I have a ADSL Broadband internet with a wireless modem.It sounds like your dongle is working. Your problem may be your network setup. Can you access the wireless modem setup? Usually you get to it by entering the IP address 192.168.1.1 into your browser. If you know how the modem is operating, you can probably adjust your settings to match.

If the Windows machine is working, look at its network settings. If I remember correctly, you find them in the Network control panel, select the TCP/IP service, Properties, and then (I can't remember) maybe the General tab, and either Advanced or Details.

---

### Post by ThePinkWitch on 2008-02-12
> **Pelham123 said:**
> With the WG111 v2 Dongle?



Ina terminal, type in the following commands individually and paste output into reply:

lsusb
ndiswrapper -l
iwconfig




Does this mean you have *some* internet access, ie - you can browse the web?

Hi thanks for replying :)

Yes "Dongle" is working. What's been happening is..first install of Ubuntu I went on forum and got instructions on ndiswrapper etc and how to set up network and after a few days it would go on but it wouldn't stay on more than a few minutes then it disconnects and won't reconnect. This is where I got in trouble I think.  I started messing with all the different settings trying to get it to work again. It only works on roaming. The Windows machine is set up for access point, DHCP whatever I went to TCP/ICP properties it's all Automatic DNS etc. It has a WEP key thing with passphrase. Do you think it's because  my Ubuntu machine is a different name to the original machine set up with this network. I have re-installed Ubuntu 6 times and tried different names for host name. The network worked for 15-20 once but when I started Firefox it dropped out immediately. Itried disabling the IPv6 in Firefox like someone said, but I haven't been able to get on the internet to see if it worked.it won't work at all now. At the momnet i'm back to using Network manager.

---

### Post by ThePinkWitch on 2008-02-12
kayte@ip6-localhost:~$ lsub
bash: lsub: command not found
kayte@ip6-localhost:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 062a:0003 Creative Labs 
Bus 001 Device 003: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 001: ID 0000:0000  
kayte@ip6-localhost:~$ ndiswrapper -l
kayte@ip6-localhost:~$ ndiswrapper 
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
kayte@ip6-localhost:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I hope this helps.

---

### Post by ThePinkWitch on 2008-02-12
> **dstew said:**
> It sounds like your dongle is working. Your problem may be your network setup. Can you access the wireless modem setup? Usually you get to it by entering the IP address 192.168.1.1 into your browser. If you know how the modem is operating, you can probably adjust your settings to match.

If the Windows machine is working, look at its network settings. If I remember correctly, you find them in the Network control panel, select the TCP/IP service, Properties, and then (I can't remember) maybe the General tab, and either Advanced or Details.

Thanks for reply :)

Yes dongle is working. I checked the TCP/IP and it's DHCP and all Automatic. The Netgear screen says Access point, WEP KEY and has passphrase checked. In Zonealarm, in trusted zone, the only one listed was loopback adapter and now there is one called New Network, thats in there as active network and the original one called loopback adapter is listed as inactive. oops. What have I done lol. I accidently made a new network.

---

### Post by ThePinkWitch on 2008-02-12
hmm maybe should try re-install number 7??  :lolflag:   Try once more...](*,)

---

### Post by dstew on 2008-02-12
You want the New Network. The loopback adapter is just a network that connects to itself, which you can use for testing. My guess is that your dongle works, the driver is OK, but that you need to get the proper configuration. Make sure your WEP key is correct. That is usually the sticking point. A WEP key can either be hexadecimal, or ASCII (text). I think the term "passphrase" refers to a text WEP key. So, you can have a 128-bit hex key that will look like 26 numbers and the letters a through f. That is not a passphrase, but a hex key.

---

### Post by ThePinkWitch on 2008-02-12
> **dstew said:**
> You want the New Network. The loopback adapter is just a network that connects to itself, which you can use for testing. My guess is that your dongle works, the driver is OK, but that you need to get the proper configuration. Make sure your WEP key is correct. That is usually the sticking point. A WEP key can either be hexadecimal, or ASCII (text). I think the term "passphrase" refers to a text WEP key. So, you can have a 128-bit hex key that will look like 26 numbers and the letters a through f. That is not a passphrase, but a hex key.

There is a WEP key with a lot of letters and numbers but on Netgear Smart Wizard WEP is ticked with Passphrase ticked and the passphrase is like a password, which I know. On Network Manager I put that in and it sometimes connects brieifly. I've tried WiFi Radar and Wicd but gone back to  Network manager because it's easier and will connect sometimes although not for long. I think I need to delete completely the Wireless network Connection on my first computer with WinXp and start a completely new network but i'm scared I'll stuff it up and have no internet at all :( Like I mentioned before I had a guy from a computer shop set it up in the first place. I've rung him three times but he is too busy to come out. If I can't get it to work I'll just have to have Ubuntu on the second machine with no "net" which is pretty useless.

 Thanks for you're help :)

---

### Post by ThePinkWitch on 2008-02-12
Installing Ubuntu again because I realised that the Network works for a while after I reinstall it. It's after I install all the updates it won't work at all. So I'll try again after install. Thanks

---

