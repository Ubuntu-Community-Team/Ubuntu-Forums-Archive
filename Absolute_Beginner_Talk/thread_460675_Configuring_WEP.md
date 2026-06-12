---
title: "Configuring WEP"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by hkahwaji on 2007-05-31
I just installed Ubuntu 7.04 and I am fairly happy about the OS so far. I was able to configure my ATI X1400 card and ofcourse the next thing is configuring my Intel 3945 a/b/g card. 

I was able to set the logical port of the wireless card to wlan0. Initially it was defaulting to eth0 so I made the changes in the /etc/iftab file and passed wlan0 with the MAC address of the Intel wireless card. 

Then I modified the /etc/network/interfaces and listed my wireless-essid under the wlan0. Here the output of cat /etc/network/interfaces

auto lo
iface lo inet loopback

iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys




auto eth1

iface eth0 inet dhcp


I now am able to connect to the linksys wireless network if the security is disabled. I want to turn on WEP on the wireless router; however I am not sure how to pass the key in the /etc/network/interfaces file. 

I tried to install network-manager which I am sure that I did, but I read that if you alter the interfaces file then the Network-Manager will not manage your devices anymore. I do not see the icon and I tried to add.

I would appreciate if someone can assist in how to pass the WEP key in the file.

Thanks

Information:
Intel 3945 abg
Linux Driver

---

### Post by kernel tom on 2007-05-31
my favorite way of doing it is via the wlassistant

if you know ur key, then ur set... 

connect to the internet anyway you can

then 

sudo apt-get wlassistant

and run it as root

sudo wlassistant

it will bring up your connection, and all others in ur range, and step you thru setting up WEP secure connections, and save ur settings

---

### Post by hkahwaji on 2007-06-01
I will attempt doing that. Is wlassistant like iwlist scan or is it a GUI application that will allow me to connect to wireless network using the SSID and WEP Key.

Also, how to uninstall in case I want to remove it. is it sudo apt-get uninstall

Thanks

---

### Post by Inxsible on 2007-06-01
I would advise you to use WPA if your router and card support it. WEP is easily cracked these days even if you have a 128-bit encryption

---

### Post by hkahwaji on 2007-06-01
I agree with you on that, but I want to see how WEP works and then tackle WPA2-AES. 

Thanks

---

### Post by kernel tom on 2007-06-02
to remove any package its 

sudo apt-get remove "package"

so in this case

sudo apt-get remove wlassistant

---

