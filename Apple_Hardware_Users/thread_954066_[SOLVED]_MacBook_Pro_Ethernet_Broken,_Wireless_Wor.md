---
title: "[SOLVED] MacBook Pro Ethernet Broken, Wireless Works"
date: 2008-10-20
forum: Apple Hardware Users
---

### Post by makajawanjack on 2008-10-20
I have the bizarre problem that on my MacBook Pro (2,1), the wireless works splendidly, but the wired cable fails to connect. The port is fine, I checked it on a Dell Ubuntu machine. Plugging and unplugging the cable has no effect in the NetworkManager. I am using Ubuntu Hardy Heron.

Here is the output of my lscpi:
```
jack@nbitesunroll: ~ $ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0c:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

Any advice or direction would be much appreciated. Let me know if I should post any other info. Thanks!

---

### Post by cyberdork33 on 2008-10-20
does it work in OSX?

What is the output of 'ifconfig'?

What is the output of 'lsmod |grep sky2'?

---

### Post by makajawanjack on 2008-10-20
> **cyberdork33 said:**
> does it work in OSX?

What is the output of 'ifconfig'?

What is the output of 'lsmod |grep sky2'?

It worked in OSX. It has sporadically come to life in Ubuntu as well, sometimes after being on for a few hours or a day.

```
jack@nbitesunroll: ~ $ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:16:cb:89:e7:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:258 (258.0 B)
          Interrupt:16 





```

```
jack@nbitesunroll: ~ $ lsmod | grep sky2
sky2                   47620  0 

```

---

### Post by makajawanjack on 2008-10-20
It also once worked when I reversed the ethernet cable. (?) That one really threw me for a loop (it's a normal cable, no crossover).

---

### Post by cyberdork33 on 2008-10-20
> **makajawanjack said:**
> It also once worked when I reversed the ethernet cable. (?) That one really threw me for a loop (it's a normal cable, no crossover).

In that case, it sounds more like a bad cable / jack. Can you try another cable and see if you have the same problem.

---

### Post by makajawanjack on 2008-10-20
So, this is strange, but I'm going to mark it solved. When plugged into a different port with a different cable (that another MacBook had been using), the ethernet worked. Then when replugged into the *very same* port and cable, it worked again. Oh well. Thanks a lot!

---

