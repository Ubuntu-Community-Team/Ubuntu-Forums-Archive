---
title: "Tried everything I could find, and still no eth0 interface! Please HELP!"
date: 2011-11-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by FuriaeIntus on 2011-11-09
Hello all. 

I have tried everything I could find, and nothing has worked. So here goes...

I have a new Asus P5G41t-M LX motherboard that was installed using my old harddrive.. We installed Ubuntu 10.04, 64-bit... and I have no Internet connection. It simply acts as if the computer is not plugged into my LAN. In my search I've learned quite a bit, so here is the information I believe I will be asked for: 


ifconfig shows: 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)


cat /etc/network/interfaces shows:

auto lo
iface lo inet loopback


lshw -C network shows:

  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:febc0000-febfffff ioport:ec00(size=128)

This is going to drive the two of us mad..... anyone know how to help?

---

### Post by pmblakely on 2011-11-14
Hello,

I've just been battling for most of today with exactly the same problem (same motherboard, and Lucid 64-bit)

I eventually got it to work by downloading AR81Family-linux-v1.0.1.14.tar.gz from:

[http://code.google.com/p/kyosls/downloads/detail?name=AR81Family-linux-v1.0.1.14.tar.gz&can=2&q=](http://code.google.com/p/kyosls/downloads/detail?name=AR81Family-linux-v1.0.1.14.tar.gz&can=2&q=)

(I had tried several previous versions of this driver, including the one that came on the motherboard CD, none of which worked.)

then, I followed instructions from [http://ubuntuforums.org/showthread.php?t=1476231&p=9257690](http://ubuntuforums.org/showthread.php?t=1476231&p=9257690)

I then had to reboot, but after that it worked and I got the network connection back.

If your new connection comes up as anything other than eth0, then you can edit
/etc/udev/rules.d/70-persistent-net.rules
and comment out (#) the current lines beginning with SUBSYSTEM, to stop Linux trying to start up the previous ethernet card with the old MAC address.

(I also had to reinstall the graphics driver, but that might have been because it was the Nvidia proprietary one.)

Hope this helps.

---

