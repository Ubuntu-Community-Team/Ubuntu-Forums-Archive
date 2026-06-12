---
title: "wake on lan and Ubuntu PPC"
date: 2008-05-04
forum: Apple Hardware Users
---

### Post by meg23 on 2008-05-04
I am running a G4 450 MHz PPC with Feisty and OS X installed on two separate harddrives. OS X's wake on lan is 

enabled and works when I send a packet with wakeonlan, however, when Ubuntu is shutdown on the machine (which 

is the default hard disk), sending a wake on lan request does not start up the system. Because of this, it 

leads me to believe that something is improperly configured on the Ubuntu hard disk to allow wake on lan. Has 

anyone had similar problems? Is there anything in particular, besides BIOS, that needs to be configured to 

allow wake on lan? Additionally, is there any accessible feature in OPENfirmware to allow wake on lan.

---

### Post by meg23 on 2008-05-05
Here is the output from sudo ethtool eth0. 

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
        PHYAD: 0
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

---

### Post by stream303 on 2008-05-05
I noticed a little tool called "etherwake" has a ppc port for it, and see that 1.09 is available in Hardy PPC when I browsed with Synaptic.

The mention of bios in the description threw me off since we are openfirmware, but perhaps this might work for ppc?

UPDATE - upon further inspection, it appears that this utility only allows you to send the magic wakeup packet from the machine, not actually respond to it.

Aha, this looks good though I'm going to have to go through it a few times and see if it works on ppc.
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=202174](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=202174)

---

### Post by meg23 on 2008-05-05
If you do get wake on lan to work please post the output of sudo 

ethtool eth0 for comparisons sake. I am interested to see what the 

transceiver line reads. The transceiver should be listed as 

internal but it is not. I am not sure if this would make a 

difference.

---

### Post by stream303 on 2008-05-05
Here's my ethtool eth0 on my G5 iMac using a Sun GEM card:
```
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
	PHYAD: 0
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes
```

I was able to set the Wake-on paramater from "d" to "g" by using
```
sudo ethtool -s eth0 wol g
```

But I noticed that after reboot, it reverted back to "d" again.  Maybe there is something about the halt that needs to be addressed so it will keep this setting.

This is a bit new to me - I guess you need a "magic packet" specifically addressed to the machine to wake it up as well, rather than just detecting overall lan activity?

And I wonder if my card is even supported - I took a look at /usr/share/doc/ethtool/README.Debian and my Sun GEM is there, but I don't think I have the gigabit ethernet card...

---

### Post by meg23 on 2008-05-05
My ethtool option for wol has a script installed to keep the 

settings, however, the machine will not boot up at all.

---

### Post by meg23 on 2008-05-05
Do you have OS X installed along with Ubuntu? If so, how are the 

partitions set up? My Mac PPC will wake on lan with OS X.

---

### Post by stream303 on 2008-05-05
I used to dual-boot it, but lately I just run Linux on the internal drive, and when I need OSX, I just boot from an external firewire drive I loaded osx onto - using the alt/option key to choose it at boot time.

When finished, back into the drawer.. :)

---

