---
title: "Gigabit not working on Feisty/G4 400"
date: 2007-06-02
forum: Apple PPC Users
---

### Post by webaake on 2007-06-02
I get no gigabit speeds, only 100 mbit with Ubuntu 7.0.4 on my G4 400 mhz (with AGP and ADC).
I just bought a 3com gigabit switch and gigabit card to my other machine in the network. They seem reporting fine at 1 GB speeds. Some info;

ethtool -i output;

 sudo ethtool eth0
Password:
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


sudo lshw -C network;

*-network
       description: Ethernet interface
       product: UniNorth GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@21:0f.0
       logical name: eth0
       version: 00
       serial: 00:30:65:55:9f:68
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.0.250 latency=16 link=yes maxlatency=64 mingnt=64 multicast=yes port=MII speed=100MB/s
       resources: iomemory:f5200000-f53fffff irq:41

I've searched the web a lot, without finding any tweaks or any new drivers to compile. So I'll be more than grateful for any hints!

Regards,

Ake S., Sweden

---

### Post by scorpion-kde on 2007-06-02
It's the same way on my G4.  I want my gigabit!

---

### Post by webaake on 2007-06-03
Oh, I'm not alone! That feels a little bit better already! I've just invested some dollars in new Gigabit gear and can't use its potetential at all.

By the way, I've taken a look inside the sungem.ko modulefile and it said it could do gigabit in the code, but as you can see above, Ubuntu doesn't aknowledge that.

I'm seriously considering a switch to YellowDog linux (5.01). I've used it before on a PPC7600 (YDL 2.0), and I think it supports Apple hardware better.

A sidenote;  many many forum posts concerning Ubuntu ends without resolution. Either the original poster gave up or didn't report the results of the problem solving. So, you can google all day and night and just run into dead ends all the time!

Or, maybe one should try like Ubuntu 6.06 LTS ???

---

### Post by stmiller on 2007-06-03
> **webaake said:**
> 
I've searched the web a lot, without finding any tweaks or any new drivers to compile. So I'll be more than grateful for any hints!

Regards,

Ake S., Sweden

Hmm interesting. I don't have any gigabit gear to test, but yeah this driver is built in the Linux kernel. There might be some other kernel configurations to get gigabit enabled, possibly. I'll poke around.
Otherwise you'll have to try to get in touch with the sun gem kernel module developer list. (I'm not sure who maintains it.)

---

### Post by stmiller on 2007-06-03
Browsing a make menuconfig, the part about the sungem module has this attached:

>  CONFIG_SUNGEM:                                               

Support for the Sun GEM chip, aka Sun GigabitEthernet/P 2.0.  See also 
<[http://www.sun.com/products-n-solutions/hardware/docs/pdf/806-3985-10.pdf](http://www.sun.com/products-n-solutions/hardware/docs/pdf/806-3985-10.pdf)                                                                          
  Symbol: SUNGEM [=y]                                                     
  Prompt: Sun GEM support                                                 
    Defined at drivers/net/Kconfig:560                                
    Depends on: NET && NETDEVICES && !UML && NET_ETHERNET && PCI             
     Location:                                                                
       -> Device Drivers                                                      
         -> Network device support                                            
           -> Network device support (NETDEVICES [=y])                        
             -> Ethernet (10 or 100Mbit)                                      
     Selects: CRC32

So it is stuck in the section for 10/100 modules, and not gigabit modules. But the pdf doc says it is a gigabit device. Googling around I see that the person who maintains sungem is David Miller, and he makes changes right to kernel.org.

---

### Post by webaake on 2007-06-03
Thx for the reply! Really interresting hints! I'll go directly to the site you recommended.


I'm also willing to compile my own kernel, if I know it's worth it. I've done it before a long time ago.


Best Regards,

Ake Svensson, Sweden

PS Found the link to the actual sungem.c code;

[http://www.csie.ntu.edu.tw/~b92101/uclinux-dist/linux-2.6.x/drivers/net/sungem.c](http://www.csie.ntu.edu.tw/~b92101/uclinux-dist/linux-2.6.x/drivers/net/sungem.c)

And there it says it CAN do gigabit!!? Weird!

---

### Post by webaake on 2007-06-03
SOLVED !!


Solved but not happily; after a close look at the motherboard I could see that it has the BCM5201 ethernet chip wich doesn't provide gigabit. 

You have to have at least the bcm54xx chip for GB speeds.


I could get all this thanks to stmiller! You pointed me to the right site and from there I found the code for the driver and in that code were comments about different chips.


So, it is solved, but not any fun. Hope this thread will be of help for other G4 owners.

The fun part is that I can now stick to Ubuntu feisty, and don't have to go for other distros.

Thx again!
PS Is a D-link DGE 528T something to try under Feisty?

---

### Post by stmiller on 2007-06-03
Ah! Well thanks for that info. Looks like my circ. 2002 G4 TiBook is out of luck. :(

---

### Post by webaake on 2007-06-04
Hi!

Turns out I have this model:

[http://support.apple.com/specs/powermac/Power_Mac_G4_AGP.html](http://support.apple.com/specs/powermac/Power_Mac_G4_AGP.html)


No GB-card there.......


Just bought a Dlink 528T on Ebay instead. Hope it'll work.

...

---

