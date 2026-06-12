---
title: "setting up wireless need lots of help"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by tibby_ on 2007-11-09
so the lspci says:
network controller: broadcom coporation bcm4318 [airforce one 54g] 802.11g wireless lan controller (rev 02)
but now what my network settings under wireless still says the network interface is not configured i really need some step by step help

---

### Post by Pumalite on 2007-11-09
Post:

lshw -C network

---

### Post by tibby_ on 2007-11-09
k now what should i do???

---

### Post by Pumalite on 2007-11-09
Copy and paste the output here.

---

### Post by tibby_ on 2007-11-09
it says : you should run this program as a super-user.
   *-network:0 disabled
         description: ethernet interface
         product: bcm4401-b0 100base-tx
         vendor: broadcom corporation
          Physical id:0
         bus info : pci@0000:03:00.0
          logical name: eth0
         version 02
          serial: 00:12:3f:e2:a8:8c
          width: 32 bits 
          clock: 33mhz
          capabilities: bus_master cap_list ethernet physical
          configuration: broadcast=yes driver= b44 driverversion-1.01 latency=64 module=b44 multicast=yes
    *-network:1 disabled
           descriptioin: wireless interface
           product: bcm4318 [airforce one 54g] 802.11g wireless lan controller 
           vendor: broadcom corporation
           physical id: 3
           bus info: pci@0000.03:03.0
           logical name: eth1
            version: 02
           serial 00:14:a5:0b:73:4e
           width: 32 bits
           clock: 33mhz
           capabilities: bus_master ethernet physical wireless
           configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-rt latency=64 module bcm43xx multicast=yes wireless ieee 802.11b/g


k thats what it says now what should i do??

---

### Post by Pumalite on 2007-11-09
Follow the instructions:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by jpittack on 2007-11-09
This guide is specific to your card.

[http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318]("http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318")

Ask any questions you might have in the linked thread, as the OP should be able to provide the answer.

---

### Post by Pumalite on 2007-11-09
'God doesn't play dice with the Universe'

---

### Post by tibby_ on 2007-11-09
man i really don't know if it worked i tried both of them but i definatley don't see any difference. i can't find the roam button to roam for connections

---

### Post by Pumalite on 2007-11-09
Here you have more links to read and learn:

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

