---
title: "[SOLVED] Howto: Configure network cards"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by daimaru on 2007-12-15
This is meant to be a small networking howto and troubleshooting tutorial. I am actually posting this so I can just link to it in future for some networking questions. Yeah I know I'm lazy :D

The following will be the default values I'll use throughout this howto for the router's, computer's and namservers IP address. 
[COLOR=Red]router: 192.168.178.1
nameserver: 192.168.178.1
computer: 192.168.178.2[/COLOR]

The Network Interface used:
[COLOR=Red]eth0[/COLOR]

If you are using different Network devices or router/nameserver IP please modify accordingly.

Everything is of course supposed to be typed into the terminal. "Applications-->Accessories-->Terminal"

[COLOR=Blue]**List the network adapters**[/COLOR]:
```
ifconfig -a
```**[COLOR=Blue]List wireless network adapters[/COLOR]**
```
iwconfig
```**[COLOR=Blue]To bring up your device[/COLOR]**
```
sudo ifconfig eth0 up
```**[COLOR=Blue]To shut down a device[/COLOR]** 
```
sudo ifconfig eth0 down
```You will need an IP address assigned to your network interface (NIC) in order to be able to connect to your router / the internet.
**[COLOR=Blue]Assign an IP automatically[/COLOR]** (assuming DHCP-Server is activated in your router)
```
sudo dhcpcd eth0
```[B][COLOR=Blue] Assign an IP manually:
[/COLOR][/B]```
sudo ifconfig eth0 192.168.178.2
```If your assigning manually you can choose any number between 2-254 as long as it's not already used by another computer on your network.
(in this example 192.168.178.2 will be your computer's network interface IP. You will have to modify it to match your networks IP Range. This depends on which IP your router is using. Common IP's for routers are 192.168.1.1 ; 192.168.2.1 ; 192.168.0.1 ; 192.168.178.1  check your manufacture's website or google your "routerName + default ip address" to find out your router's IP if you don't know it). 
If everything already works your routers IP should be listed as the gateway when you type.
[COLOR=Blue]**Check your routing table:**[/COLOR]
```
route
```If you have an IP address assigned, but you can still not access the internet you may have to manually add a default gateway.
**[COLOR=Blue]Adding Gateway:[/COLOR]**
```
sudo route add default gw 192.168.178.1 eth0
```Now you should be connected to the internet. If you can ping IP addresse's (ping 208.65.153.253) but you can not ping (ping [www.youtube.com]("http://www.youtube.com")) then your nameserver is not defined. 
**[COLOR=Blue]Adding Nameserver:[/COLOR]**
```
sudo echo nameserver 192.168.178.1 > /etc/resolv.conf
```[B][COLOR=Red]Wireless configuration:

[/COLOR][/B]This time the wireless network interface name will be ath0 (cause I got an atheros card)

**[COLOR=Blue]Configure your wireless card automatically:[/COLOR]**
```
 sudo dhcpcd ath0
```**[COLOR=Blue]Adding your ESSID manually:[/COLOR]**
```
 sudo iwconfig ath0 essid <myEssid>
```**[COLOR=Blue]Adding WEP key manually:[/COLOR]**
```
sudo iwconfig ath0 key <WEPkey>
```Hope that helps the next time you have trouble with your network card. It works for me :mrgreen:

PS: I don't know how to set WPA stuff manually, except by using wpa_supplicant.conf file, but I don't think gutsy is using wpa_supplicant.conf to store wpa info. So where do you define WPA stuff manually in Gutsy ?

---

