---
title: "newbie ethernet address"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by bluepepper on 2007-09-29
first time linux user , please help!

  my ethernet address keeps changing after every boot , i need a fixe ethernet address for hardware lock for maya, how to work this one out???

eth1      Link encap:Ethernet  [COLOR="Red"]HWaddr A6:08:FD:B5:5F:B2  [/COLOR]
          inet addr:192.168.11.41  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::a408:fdff:feb5:5fb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1869 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1837 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1668422 (1.5 MiB)  TX bytes:287428 (280.6 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

hwaddr keeps changing, i have a wired adsl cionnection.

thanks
:(

---

### Post by Kilz on 2007-09-29
That depends. Did you setup a home network with a router, or is your computer hooked strait to the adsl modem? If its strait to the modem you may not be able to do it because the address is under control of your isp. If you setup a home network with a router you will have to configure the router/network to use static addresses. Your router manual might be able to help you do that.

---

### Post by Natr0n on 2007-09-29
> 
hwaddr keeps changing


I don't see how the OP's HWaddr is changing on reboot; regardless of router/network configuration. If the OP meant "IP address" that might make some sense.

---

### Post by bluepepper on 2007-09-29
thanks for your replies, yes i have home network with my pc connected on wire and another pc via wireless, to an air sation modem with g/b bandwidth.
i am dual booting xp pro and ubuntu, xp sees the network card but ubuntu does not i wonder what may be the reason.

mobo asus p5k
built in lan attansic gigabit L1


hth


thanks again:confused:

---

### Post by louieb on 2007-09-29
> **bluepepper said:**
> ... wireless, to an air sation modem with g/b bandwidth... xp sees the network card but ubuntu does not i wonder what may be the reason.
If you have internet with Ubuntu then it sees your card just fine.
```

eth1      Link encap:Ethernet  [COLOR=Red]HWaddr A6:08:FD:B5:5F:B2  [/COLOR]
          inet addr:192.168.11.41  

```the HWaddr is the **MAC** address of your card. It is unique to that card: no other card in the world has that address. The only way it can change is if you have two cards or the card you have is screwed up. There should be a sticker with the **MAC** address somewhere on th PC. If it doesn't match what ifconfg in Linux or ipconfig in XP displays  then you probally have a hardware problem.

 The inet addr is the current IP address as assigned by your DHCP server. (Probably your modem/router is your DHCP server).  Through my routers lan IP setup I can make it assign a certain  IP address based on the **MAC** address of the card. Thats how my home network Ip address are assigned.

---

### Post by bluepepper on 2007-09-29
tahnks i shall give it a try and just install anew ethernet card



:???::???:

---

### Post by jcliburn on 2007-09-30
Your kernel is apparently old.

For historical context, early versions of the atl1 driver tried to read the MAC address only from eeprom, and if it didn't get a valid address, it grabbed a random one provided by the kernel. We discovered that some motherboards didn't store the MAC address in the NIC's eeprom, but instead the BIOS dumped the MAC address directly into a register on the NIC.  For these motherboards, the user experienced the variable MAC address issue.  We resolved it by a driver change in February 2007.

```

commit fd8c5a7da3c48e53c7859d9f0c1d82ba02ca0a20
Author: Jay Cliburn <jacliburn@bellsouth.net>
Date:   Wed Feb 14 20:14:55 2007 -0600

    atl1: read MAC address from register
    
    On some Asus motherboards containing the L1 NIC, the MAC address is
    written by the BIOS directly to the MAC register during POST, and is
    not stored in eeprom.  If we don't succeed in fetching the MAC address
    from eeprom or spi, try reading it directly from the MAC register.

```

If you're using a recent kernel and you're encountering a random MAC address, I'd like to know more about your setup.

---

### Post by radu.c on 2008-06-10
I have an ASUS computer that also changes its MAC address when running Linux. The network card uses the atl1 driver. Happens in 8.04 too.

It seems that the atl1 driver no only doesn't get the correct MAC address, but moreover it writes a new, random one in the EEPROM. I say that because if I keep rebooting it, without loading the atl1 driver, the PXE-reported MAC address remains the same. After the atl1 driver is loaded, the PXE MAC changes.

Any ideas why this behavior?

---

### Post by jcliburn on 2008-06-10
I'm not an Ubuntu user, so I don't know which kernel Ubuntu 8.04 uses.  Can you tell me which kernel you're running?  Also, what is your motherboard model number?

---

### Post by radu.c on 2008-06-10
> **jcliburn said:**
> I'm not an Ubuntu user, so I don't know which kernel Ubuntu 8.04 uses.  Can you tell me which kernel you're running?  Also, what is your motherboard model number?

2.6.24 is the kernel in 8.04. But it did the same with 2.6.22, which was in 7.10.

I just unplugged the power cord form the machine, then plugged it back in, and the MAC got restored to the original one. Booting from the 8.04 LiveCD changes the MAC address and stores it somewhere where the BIOS PXE bootloader can read it later. The generated MACs don't follow any pattern, and seem random.

This is an ASUS Esentio 5110 machine, details here: [http://asus.com/products.aspx?modelmenu=2&model=2211&l1=14&l2=156&l3=680&l4=0](http://asus.com/products.aspx?modelmenu=2&model=2211&l1=14&l2=156&l3=680&l4=0). I don't know what motherboard it is using. The manual doesn't specify, and I'm not at liberty to open it up.

Seems more like a driver problem than a card problem in this case.

---

### Post by jcliburn on 2008-06-10
> **radu.c said:**
> Seems more like a driver problem than a card problem in this case.

Thanks for the info.  I'm not familiar with your machine, so we might be encountering something new.

The atl1 driver doesn't write anything to eeprom.

Are you in a position to build a new driver for this machine if I provide you with versions to test?

---

### Post by radu.c on 2008-06-10
Well, I found what the problem is: the driver detects an EEPROM, but the MAC address stored there is all zeroes. The problem with the driver is that it doesn't continue with the other two possibilities (SPI, and BIOS register) if the EEPROM contains an invalid value.

The patch is very simple actually:

```

diff -r 59a7d1c87a50 drivers/net/atl1/atl1_hw.c
--- a/drivers/net/atl1/atl1_hw.c	Tue Jun 10 13:34:40 2008 +0000
+++ b/drivers/net/atl1/atl1_hw.c	Tue Jun 10 13:53:16 2008 +0000
@@ -250,7 +250,6 @@ static int atl1_get_permanent_address(st
 			memcpy(hw->perm_mac_addr, eth_addr, ETH_ALEN);
 			return 0;
 		}
-		return 1;
 	}
 
 	/* see if SPI FLAGS exist ? */

```
Who submits it to the kernel people?

---

### Post by jcliburn on 2008-06-10
> **radu.c said:**
> Who submits it to the kernel people?

I maintain the driver, so I'm the one who submits it for kernel inclusion.

Have you actually tested the driver with your patch to verify it works correctly?

The code is written the way it is today because an all-zeros mac address coming out of eeprom is something we've never seen, and is considered to be an error condition.  The (now flawed) logic was this:  either the eeprom exists and there's a valid mac address stored therein, or the eeprom doesn't exist and we check the SPI or the mac station address register.

I guess now you've shown us that the eeprom can actually contain an illegal mac address that shouldn't be considered an error.

I really appreciate your report.  If you'd like me to credit you in the kernel patch, I'll need your name and email address.  You can send it to jcliburn at gmail dot com if you wish.

---

### Post by radu.c on 2008-06-10
Yes, I actually tested it before posting the reply. The machine is running fine now, and its shipped MAC address stays the same across reboots.

My name is Radu Cristescu, and my e-mail address is advantis at gmx dot net. (These details will show up in the kernel changelog anyway if you mention me, so I guess it's not much point in sending you a separate e-mail)

---

### Post by jcliburn on 2008-06-10
> **radu.c said:**
> (These details will show up in the kernel changelog anyway if you mention me, so I guess it's not much point in sending you a separate e-mail)
Right.

Thanks again for your report.  You'll be cc'd on all the traffic relating to this fix.

---

### Post by jcliburn on 2008-06-24
Random MAC address fix has been added to mainline (2.6.26-rc7) and stable (2.6.25.9) kernels.

[http://lkml.org/lkml/2008/6/20/421](http://lkml.org/lkml/2008/6/20/421)
[http://lkml.org/lkml/2008/6/24/413](http://lkml.org/lkml/2008/6/24/413)

(search these links for the string "atl1")

---

