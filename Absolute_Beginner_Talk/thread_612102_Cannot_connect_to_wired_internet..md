---
title: "Cannot connect to wired internet."
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by DavidLamp on 2007-11-13
Hello,

I have installed Ubuntu 7.04. I am unable to access the internet.  I am using an ethernet connection.  The DHCP server is assigning an IP address to the machine. It knows the correct server information.  I try to ping the dsl modem and am unable to get a response.  I was able to ping once properly.  I do not know why.

Please advise.

Thank You,

David Lamp

---

### Post by reckless2k2 on 2007-11-13
could you please post the results of the following 2 things from the teminal:

this'll show us if you've got a detected card
```
lspci -v
```

this will show us if the OS is detecting the card or what the card prob might be
```
ifconfig
```

---

### Post by DavidLamp on 2007-11-13
davidlamp@Office1:~$ lspci -v

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)

        Flags: bus master, 66MHz, fast devsel, latency 0

        Memory at e8000000 (32-bit, prefetchable) [size=32M]

        Capabilities: <access denied>



00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: 66MHz, fast devsel



00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: 66MHz, fast devsel



00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: 66MHz, fast devsel



00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: 66MHz, fast devsel



00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: 66MHz, fast devsel



00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: bus master, 66MHz, fast devsel, latency 0

        Capabilities: <access denied>



00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: 66MHz, fast devsel, IRQ 255

        I/O ports at d000 [size=32]

        Capabilities: <access denied>



00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16

        Memory at ec081000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17

        Memory at ec086000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18

        Memory at ec087000 (32-bit, non-prefetchable) [size=256]

        Capabilities: <access denied>



00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16

        Memory at ec080000 (32-bit, non-prefetchable) [size=4K]

        I/O ports at d400 [size=8]

        Capabilities: <access denied>



00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 255

        Memory at ec000000 (32-bit, non-prefetchable) [size=512K]

        Capabilities: <access denied>



00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17

        I/O ports at d800 [size=256]

        I/O ports at dc00 [size=128]

        Memory at ec082000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])

        Flags: bus master, 66MHz, fast devsel, latency 0

        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32



00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: bus master, 66MHz, fast devsel, latency 0

        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]

        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]

        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]

        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]

        I/O ports at f000 [size=16]

        Capabilities: <access denied>



00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2) (prog-if 00 [Normal decode])

        Flags: bus master, 66MHz, medium devsel, latency 32

        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32

        Memory behind bridge: ea000000-ebffffff

        Prefetchable memory behind bridge: e0000000-e7ffffff



02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3) (prog-if 00 [VGA])

        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 904d

        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10

        Memory at ea000000 (32-bit, non-prefetchable) [size=16M]

        Memory at e0000000 (32-bit, prefetchable) [size=64M]

        Memory at e4000000 (32-bit, prefetchable) [size=512K]

        [virtual] Expansion ROM at e4080000 [disabled] [size=128K]

        Capabilities: <access denied>



davidlamp@Office1:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:40:CA:89:EC:B5  

          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0

          inet6 addr: fe80::240:caff:fe89:ecb5/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:11576 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1675 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:728319 (711.2 KiB)  TX bytes:191407 (186.9 KiB)

          Interrupt:16 Base address:0x2000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:6 errors:0 dropped:0 overruns:0 frame:0

          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:1352 (1.3 KiB)  TX bytes:1352 (1.3 KiB)

---

### Post by shad0w_walker on 2007-11-13
As this is a likely thread to be attacked. Do not run any commands using the rm command. There is a spammer on the forums. Check the sticky in the newbies section.

---

### Post by DavidLamp on 2007-11-13
Now Working,

I do not know why or what has changed, I have to say it is now working.

I had pinged the router serveral times. every once and a while it would work.

I do not think I changed anything.

It appears to be working fine now. I am downloading updates without any problems.

Confused but working,

David Lamp

---

### Post by DavidLamp on 2007-11-13
Update,

Ability to use the internet comes and goes.

I do not know why this is.

It will work for a few minutes then it does not.

There are several other computers on the same network that do not have any problems.  The other computers are mac or intel machines.

Thank You and Please Advise,

David Lamp

---

