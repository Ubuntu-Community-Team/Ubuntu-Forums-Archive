---
title: "Ubuntu 7.10 slow speeds transfer from cifs share"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Hard2Hold on 2007-10-20
Just moved from RHEL 5 on my test box and so far everything is good except for transferring files from my windows file server.  I am on a full gig network.  

> Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes



My Network card is :

> 
        *-network
             description: Ethernet interface
             product: RTL-8169 Gigabit Ethernet
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: eth1
             version: 10
             serial: 00:08:54:d1:54:0f
             size: 1GB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.140 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=1GB/s


Now if I scp the file using winscp to the ubuntu box I can get a 1.4 gig files in 13 minutes.  If I use the cifs share on the ubuntu box to copy it from the windows share, I get either 

A)  it times out
B)  It transfers at 40 k and will take 12 hours.

Here is my /etc/fstab:

> 
//192.168.0.181/shared  /samba  cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0


When this box ran RHEL, I did not have any speed problems using CIFS mounts and the transferring of files back and forth.  

I have read other posts via google about users having this same problem, some have blamed the drivers for realtek, some samba but I have not found a resolution to the slowness.  Would think if it were samba, it would have also shown up on RHEL5.  

Thanks in advance.

---

