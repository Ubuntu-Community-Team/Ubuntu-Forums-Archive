---
title: "Found internal modem problem solved"
date: 2007-01-20
forum: Apple PPC Users
---

### Post by linuxppcuser on 2007-01-20
The internal modem problem solved
The internal modem worked in Kubuntu 5.04 so I got me a Live CD
booted it up let it do its thing.
I open up the terminal and typed dmesg
and there is was
 pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
 80.826155] pmac_zilog: serial modem detected
 80.826245] ttyS0 at MMIO 0x80813020 (irq = 15) is a Z85c30 ESCC - Internal modem
 80.828600] ttyS1 at MMIO 0x80813000 (irq = 16) is a Z85c30 ESCC - Infrared port

So that tells me the driver was not installed for the internal modem in Dapper Drake
I logout ejected the CD rebooted back into Dapper Drake.
Opened up a Terminal and typed dmesg 
No drivers was installed, So I typed modconf (you may have to install this) looked thru drivers until I found pmac_zilog so I installed it. So I went ahead and rebooted so that I can check the dmesg again and it loaded the internal modem driver the internal modem is now working.  If it worked in one of Ubuntu version and it did not in the other version 
Try a Live CD to see why it working and not in the other version.

linuxppcuser

---

### Post by Tommy on 2007-01-21
> **linuxppcuser said:**
> ... looked thru drivers until I found pmac_zilog so I installed it. So I went ahead and rebooted so that I can check the dmesg again and it loaded the internal modem driver the internal modem is now working.  If it worked in one of Ubuntu version and it did not in the other version 


The newer kernels (Dapper 6.06 and later) do not have the pmac_zilog module in them, but fortunately it's still included, just not loaded. All you have to do is add pmac_zilog to the /etc/modules file and after the next reboot your kernel will see it.

I am not sure what the modconf command does so your technique may be better.

---

