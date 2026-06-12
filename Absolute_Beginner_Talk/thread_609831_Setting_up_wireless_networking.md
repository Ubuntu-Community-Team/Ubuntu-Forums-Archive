---
title: "Setting up wireless networking"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by underthechair on 2007-11-11
I'm considering switching to Ubuntu from Windows XP but I can't seem wireless networking work consistently. I've attempted to follow all the online help manuals/troubleshooting guides but nothing seems to cover my problem.

I can connect to my network when i boot up, but this connection rarely lasts. I experience particular problems when returning to my computer after it has been suspended/hibernated or there is a problem affecting the whole network, but it can also happen without prompting. When it happens I cannot connect to the network (though the network manager icon may show a connection) until I restart the computer.

I'd be very grateful for any advice regarding this problem, since until it is solved there is no realistic prospect of me switching to Ubuntu. If any further information is required then I'd be happy to provide it.

Thanks.

Adam

---

### Post by matthewcraig on 2007-11-11
I am not the best person to ask about WiFi drivers.  I did want to recommend that you consider buying your next laptop from a vendor who sells Ubuntu pre-installed, and that way you will know everything works right out of the gate.  I think everyone has one or two things on their computer that they wished worked better with Ubuntu.  WiFi is one of those areas where there are some devices that will never work because of the vendors' closed-specifications.  I hope yours is not one of them!

---

### Post by underthechair on 2007-11-11
I think my wireless card is based on Ralink, so theoretically that shouldn't be a problem.

---

### Post by skanchi on 2007-11-11
What wifi card/driver and user application are you using to connect to wifi network

---

### Post by underthechair on 2007-11-11
My wireless card is a D-Link DWL-G630, which lspci says is based on the " RaLink RT2561/RT61 rev B 802.11g" chipset with the driver that came with the installation - apparently it should work out of the box. I have been using the normal Ubuntu network manager software - I wasn't aware there was another option.

---

### Post by Pumalite on 2007-11-11
Check these links and hopefully you'll find your answer:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
[http://ubuntuforums.org/showthread.php?t=586387](http://ubuntuforums.org/showthread.php?t=586387)
[https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by underthechair on 2007-11-11
Thanks, but I'm afraid none of these links address my problem.

---

### Post by Pumalite on 2007-11-11
Maybe this then:

[http://ubuntuforums.org/archive/index.php/t-4200.html](http://ubuntuforums.org/archive/index.php/t-4200.html)

---

### Post by ushills on 2007-11-11
RT61 doesn't work out of the box reliably.  I had the same connection issues,try the guide on my site at [www.ushills.co.uk/ubuntu/RT61.html](www.ushills.co.uk/ubuntu/RT61.html).

You need to install the serial monkey drivers

---

### Post by underthechair on 2007-11-12
Thanks Ushills, I think this is close to working, but it's not quite there. When I type "lsmod | grep rt" I see the new driver (rt61, 210440, 0; rt61pci, 24576, 0; rt2x00pci, 11520, 1, rt61pci; rt2x00lib, 19584, 2, rt61pci, rt2x00pci.) When I came to edit the network settings there was no wlan0 section to replace, so I copied in the one your guide suggests but when I came to restart networking I got the message "Invalid command : set. Failed to bring up wlan0." I also find that my addition of "nameserver 192.168.1.1" to the "/etc/resolv.conf" file is repeatedly reversed, seemingly by Network Manager. Do you have any further advice? Thanks.

---

### Post by ushills on 2007-11-14
> **underthechair said:**
> Thanks Ushills, I think this is close to working, but it's not quite there. When I type "lsmod | grep rt" I see the new driver (rt61, 210440, 0; rt61pci, 24576, 0; rt2x00pci, 11520, 1, rt61pci; rt2x00lib, 19584, 2, rt61pci, rt2x00pci.) When I came to edit the network settings there was no wlan0 section to replace, so I copied in the one your guide suggests but when I came to restart networking I got the message "Invalid command : set. Failed to bring up wlan0." I also find that my addition of "nameserver 192.168.1.1" to the "/etc/resolv.conf" file is repeatedly reversed, seemingly by Network Manager. Do you have any further advice? Thanks.

Okay, it looks like the driver is loading correctly, however, there are a couple of things you should try.

Enter ```
sudo iwconfig
```

check that wlan0 is correct, it may be wlan1. I would also suggest the following configuration be tried first:

```
# The wireless network interface
      auto wlan0
      iface wlan0 inet DHCP
      pre-up ifconfig wlan0 up
      pre-up iwpriv wlan0 set AuthMode=WPAPSK
      pre-up iwpriv wlan0 set EncrypType=TKIP
      pre-up iwpriv wlan0 set NetworkType=Managed
      pre-up iwconfig wlan0 essid ssid_of_your_wlan
      pre-up iwpriv wlan0 set WPAPSK="wpa_password"
```

You should also uninstall network manager with```
sudo apt-get remove network-manager-gnome
```

Post back if you have problems.

---

