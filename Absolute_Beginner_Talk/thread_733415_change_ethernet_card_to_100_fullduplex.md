---
title: "change ethernet card to 100 fullduplex"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2008-03-23
hi

my internet service has recently been upgraded from 8Mbps to 15 Mbps.

the problem is i am only able to reach speeds around 8 or so when i try the speedtests (i already checked 3 times with their customer support and they gave me their word that they had already changed the speed up to 15).

 this lead me to believe that the problem must be mine.. the modem supports speeds up to 13 (they will be changing it tomorrow with a newer model)

in fact, they stated that i need to configure my card to 100 fullduplex to be able to reach 15 Mbps.

the problem is i don't know the method to:

1) check if my card is in fact 10 halfduplex

2) in case it is indeed at 10 halfduplex, what to do to change it to 100 fullduplex.



note: i don't know if this is relevant or not but the modem is connected to a linksys router that is capable of 100 Mbps through cable and 54 Mbps through wireless.

if any of you can give me any help on how to go through step 1 and 2 i will be extremely appreciated.

regards

---

### Post by cmaranhao on 2008-03-23
bump

---

### Post by RealPSL on 2008-03-23
Use sudo /usr/sbin/mii-tool to check the link speed and duplex of your network adapter. I have provided example output below.

$ sudo /sbin/mii-tool
[sudo] password for :
eth0: negotiated 100baseTx-FD flow-control, link ok

---

### Post by cmaranhao on 2008-03-23
i forgot to say that i don't know how to work in linux.. i must be doing something wrong, i went to terminal and did like you said, it hasn't worked though. look here:

maranhao@maranhao-desktop:~$ sudo /usr/sbin/mii-tool
Password:
sudo: /usr/sbin/mii-tool: command not found
maranhao@maranhao-desktop:~$ 


i really don't have a clue what to do here.

EDIT:

i don't really know what those commands are doing, are they to know the actual configuration of the card or to change the configuration to fullduplex?

---

### Post by VirtualTiger on 2008-03-23
The following command will give you information on how your network card is setup:
```
ethtool eth0
```

This command will set it to a fixed speed of 100 mbs and full duplex, and disabled auto negotiation:
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

You'll need to research your network card to see what settings will work the best for you.

Add the command to **/etc/rc.local** so its sets it each time you restart your computer.

---

### Post by cmaranhao on 2008-03-23
aperently it is already at 100 Mbps. look at this:
> 
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 9
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes
root@maranhao-desktop:/home/maranhao# 

is it better to do the rest of the commands?

i mean these: sudo ethtool -s eth0 speed 100 duplex full autoneg off

---

### Post by dcstar on 2008-03-24
> **cmaranhao said:**
> hi

my internet service has recently been upgraded from 8Mbps to 15 Mbps.

the problem is i am only able to reach speeds around 8 or so when i try the speedtests (i already checked 3 times with their customer support and they gave me their word that they had already changed the speed up to 15).
.........

Assuming you are using an ADSL connection, there is no guarantee that your line will actually support higher sync rates.

Log into your modem and see what it says.

---

### Post by cmaranhao on 2008-03-24
i don't know how to log in the modem, like i said, my knowledge in linux is very reduced.

now, from my previous post, i believe the card is at 100 fullduplex, the only thing that is worrying me is the auto negotiation on.

should it be off? or is the card already configured properly to have speeds up to 15 Mbps?

---

