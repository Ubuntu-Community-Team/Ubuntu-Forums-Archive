---
title: "Network Commands for use in startup script?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by drafael on 2007-11-20
Hey,
Forgive me for not reading up on it and simply finding out myself but I have exams and don't really have the time right now...

The issue: Wireless. It works with ndiswrapper loaded to kernel(Hooray)! But every time I turn on this here laptop, I have to go into the network manager and set it first to "Local Zeroconf" and then back to "Static IP address" for the card to connect properly.. I may be missing something here >_>

The wireless settings have to be manual because I've turned off dhcp and ipv6 for the router due to our large and complex setup here.

Anyway, all I need are the appropriate terminal commands to set it to zeroconf and then back to static ip or something that I can put into a startup script. It's perfectly usable, just fairly irritating to have to make my touchpad mouse go up to the top corner, click, go back to the center of the screen, click, go up, click, go down, click, go down, click, go up, click, go down, click, go up, click, go down, click, go down, click, INTERNET! Haha.

Thanks in advance for any help!

---

### Post by MaximusTG on 2007-11-21
What security do you use? Wep, wpa? And do you only use the laptop on this network, or do you use it on multiple networks? Because I have a laptop that I use on my university, and because networkmanager doesn't support its security, I have the wireless card setup using a combination of the /etc/network/interfaces file, and wpa_supplicant. You can even setup different networks in wpa_supplicant, and it will roam automatically.

---

### Post by drafael on 2007-11-21
Thanks for your response - I use wep encryption and the network runs at a level that my nintendo ds supports (lowered transmit rates etc) - thankfully not too too many internet stealers in NZ. The laptop is only used wirelessly on this network - occassionally I plug in ethernet for transfer between computers on a different network range but that's it.

Had a look at /etc/network/interfaces, should I have both an "auto wlan0" and an "iface wlan0" entry? I may try removing the "auto" entry...

Thanks again

---

### Post by MaximusTG on 2007-11-21
I found this link:

[http://newbiedoc.berlios.de/wiki/How_to_set_up_a_wireless_network_card_using_drivers_from_Debian_packages#Set_WEP_encryption](http://newbiedoc.berlios.de/wiki/How_to_set_up_a_wireless_network_card_using_drivers_from_Debian_packages#Set_WEP_encryption)
section 8.8.3 contains the code you see below.

Add that to your /etc/network/interfaces file, replacing the ip-addresses with the ones that apply to you, and you also have to change the essid and the wep-key. Note that if  you input it as an ascii passphrase, it should be preceded with s:
So if you passphrase was "topsecret" it would look like this:

wireless-key s:topsecret

```

auto wlan0
iface wlan0 inet static
address 192.168.1.nnn
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
# replace mylan with the essid set up on the AP
wireless-essid mylan
wireless-mode Managed
# Set up encryption.
wireless-keymode restricted
wireless-key XXXXXXXXXX

```

---

### Post by drafael on 2007-11-21
Awesome, worked perfectly once I replaced my current entry and removed the other entry for the same card.
Thanks! :D

---

### Post by MaximusTG on 2007-11-21
That's great, nice to hear it worked for you!

---

