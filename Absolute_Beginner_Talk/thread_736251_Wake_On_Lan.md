---
title: "Wake On Lan"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Elevator_Hazard on 2008-03-26
I can't seem to get wake-on-lan to work... I have a 4s4eb2x0 bios with On LAN [Power On] and On PCI [Power On], my wake on lan cable is plugged in (I just did that today). I know the mac address to the box's eth0 (00:01:02:77:AC:A4) and I send my packets from one computer using wakeonlan (I use the default broadcast of 255.255.255.255 and use the mac address 00:01:02:77:AC:A4...), I have a WRT54G, and I've set up wake on lan using a script I found here on these forums. Then I also found that I should do "ethtool -s eth0 wol g" But it said to me "cannot get wake-on-lan settings: operation not supported"... I now see that sometimes when I have shut off the computer my router says its still connected and I see on the back of the computer that my network card thing is lighting up, but sending wakeonlan packets doesn't work. I've tried when the computer was off, in hibernation, and on suspend but it didn't work... Any ideas?

---

### Post by wormser on 2008-03-26
What is the command you are using?  Try using one like this with your ip address.

```
wakeonlan -i ipaddress 00:01:02:77:AC:A4
```

Can you post links to the script and give us more details on the machine you are trying to wake.

Update:
Found a HowTo [here]("http://ubuntuforums.org/showthread.php?t=360901&highlight=wakeonlan").

---

### Post by Elevator_Hazard on 2008-03-26
I used the command "wakeonlan 00:01:02:77:AC:A4" when the computer was powered off (I saw the network card at the back of the computer light up a little more when I sent the packet) and then when it was hibernated or suspended I tried that same command and also tried to specify its ip address ("wakeonlan -i 192.168.1.97 00:01:02:77:AC:A4").

The script I used was the one found [here](http://ubuntuforums.org/showthread.php?t=234588).

My system...
I put in the wake-on-lan cable today after I had almost forgotten about it for a year...
I have a 3c905C-TX/TX-M [Tornado] ethernet PCI card (I think its an ethernet pci card sorry I'm not too great with that stuff)
How do I know what motherboard I have? (If the bios version (4s4eb2x0) in the previous post doesn't give it away)
Need anything else? Its a pretty old computer but it supports wake on lan.

---EDIT: Oh darn... This doesn't look good...```

jake@jake-old-desktop:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes
jake@jake-old-desktop:~$
```

---

