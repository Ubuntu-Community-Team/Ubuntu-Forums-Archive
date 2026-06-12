---
title: "Help Wireless Issues"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by RKNeff on 2008-04-09
You guys have probably heard this before but i have run into a snag.  I am running Gutsy on an Acer Travelmate 2300 and almost everything works out really well.  My one problem is the wireless.  I have installed the windows driver using ndiswrapper.

my current wlan0 portion of the /etc/network/interfaces reads

auto wlan0
iface wlan0 inet static
  wireless-essid Neff's Network
  address 192.168.0.5
  netmask 255.255.255.0
  gateway 192.168.0.1
  wireless-mode Managed
  wireless-keymode open
  wireless-key XXXXXXXXXX

I've been going through these forums for the last couple of days and I can get the wireless to see what networks are out there, but I can't seem to get into the one i need to.

Any help would be greatly appreciated.

---

### Post by wieman01 on 2008-04-10
Do you want to continue doing it through command line or do you plan to use Network Manager?

It makes a difference. If Network Manager is your tool of choice, then you need to remove all these lines so that "/etc/network/interfaces" simply read:
> auto wlan0
iface wlan0 inet dhcp
NM cannot handle static IP addresses though.

Command line would be:
> auto wlan0
iface wlan0 inet static
wireless-essid [COLOR="Red"]your_ssid[/COLOR]
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1
wireless-key [COLOR="Red"]your_passphrase[/COLOR]
Avoid special characters for your SSID such as ' or ".

---

