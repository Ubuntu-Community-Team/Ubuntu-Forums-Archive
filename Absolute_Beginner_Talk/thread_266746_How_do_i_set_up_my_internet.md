---
title: "How do i set up my internet?"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by coolbian57 on 2006-09-27
Can anyone help me set up (wireless) internet on Ubuntu (dapper/current)?  I have no idea where to begin to set up my internet connection.  

I entered the iwconfig code in the terminal and nothing came up for anything.  

Do i need to get the drivers on a disc and transfer them to Ubuntu?  Or possibly my wireless card doesn't function with Linux at all.

Please help

---

### Post by llamakc on 2006-09-27
You should tell us what type of card you have, what sort of platform you are on. . .

Meanwhile, in a Terminal, type:

lspci -v 

and either cut/paste the appropriate part (if you know what it is) or paste the entire thing here wrapped in the [ code ] tags, for starters.

---

### Post by coolbian57 on 2006-09-27
I'm looking right now at a 802.11G Motorola Wireless Adapter.

I run on Windows XP (home) currently.  

I have a Motorola Wireless USB Adapter WU830G (not the same as the one above, this is the one INSIDE of the computer)

---

### Post by llamakc on 2006-09-27
So you need help setting up wireless in Windows?

Have you installed Ubuntu yet? 

We need to see the output of

lspci -v

---

### Post by coolbian57 on 2006-09-27
No no i have it set up in windows...very well too.  Ill go get the outcome of that code.  I'll be back soon.

Oh and yes i have Ubuntu installed and partitioned.

---

### Post by llamakc on 2006-09-27
Cool. The output of that code will help us determine which kernel modules need to be loaded and the next steps you may have to take. Sometimes wireless can be a PITA, sometimes not.

---

### Post by NetworkGuy on 2006-09-27
I had another post like this today.   From what I found by googling, people have not had any success with NDISwrapper or kernel drivers with the USB adapter in any distro. 

llamakc, I hope you find something to the opposite.

---

### Post by coolbian57 on 2006-09-27
Having to download Openoffice on Windows to transfer the Open Office document from Ubuntu to Windows...  Too lazy to write down and retype but it turns out that would have been 15 min faster.
](*,) ](*,)

Can't copy and paste because i have to restart my computer to get back to Windows ( to get online )

---

### Post by coolbian57 on 2006-09-27
FINALLY HERE IT IS

```
0000:00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80c5
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev f6)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80c5
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80c5
        Flags: 66MHz, fast devsel
        I/O ports at 5000 [size=64]
        I/O ports at 5040 [size=64]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80c5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80c5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80c5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at febfdc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:05.0 Ethernet controller: nVidia Corporation nForce3 Ethernet (rev a5)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80a7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at eff0 [size=8]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8095
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Memory at febff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80c5
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at ffa0 [size=16]
        Capabilities: <available only to root>

0000:00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fea00000-feafffff

0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        Memory behind bridge: fc900000-fe9fffff
        Prefetchable memory behind bridge: cc800000-ec7fffff

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Expansion ROM at fe9e0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:05.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
        Subsystem: Agere Systems: Unknown device 044c
        Flags: bus master, medium devsel, latency 64, IRQ 255
        Memory at feaff400 (32-bit, non-prefetchable) [size=256]
        I/O ports at dff0 [size=8]
        I/O ports at d800 [size=256]
        Capabilities: <available only to root>

0000:02:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, medium devsel, latency 64, IRQ 185
        Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
        Memory at feaf8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>
```

---

### Post by coolbian57 on 2006-09-27
I don't know what any of that means really.

---

### Post by coolbian57 on 2006-09-27
Can anyone help me?>

---

### Post by ashokpappu on 2006-09-27
try this command and let me know what the output is 
u should get some output like this.  
$ /sbin/ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:3D:EA:13:67
          inet6 addr: fe80::20f:3dff:feea:1367/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:352782 errors:204132 dropped:0 overruns:0 frame:204132
          TX packets:3 errors:123 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:21214159 (20.2 MiB)  TX bytes:230 (230.0 b)
          Interrupt:193 Memory:f8a60000-f8a70000

---

### Post by coolbian57 on 2006-09-27
i have to go right now but i will try that tommorrow and Message you the details and post them.

---

### Post by coolbian57 on 2006-09-27
unfortunatley i think my card won't work with Linux.  I haven't installed the drivers yet but i don't know how to.

---

### Post by coolbian57 on 2006-09-28
Back

---

### Post by coolbian57 on 2006-09-28
I now have NDIS installed...  Can anyone tell me how to get the GUI interface for it?  I'm new to Linux, so I work better with the GUI interface.

---

### Post by coolbian57 on 2006-09-28
How do i get the Driver for my Device?  I have the PCI ID's now...

10de:00d6 (ethernet)
11cl:048c (modem)

Will i have to do this from the terminal?

---

### Post by llamakc on 2006-09-28
Are you saying you installed ndiswrapper?

Please give us the full output of:

ifconfig

Also, the GUI for networking is in SYSTEM | ADMINISTRATION | NETWORKING (in GNOME)

---

### Post by coolbian57 on 2006-09-28
Ok, I'll go get the results of that.  I'm beginning to think that my wireless card does not work with Linux, because I looked online and it said you "must have Windows".  It didn't say it was only compatable with Windows, but it said you "must have Windows" and it did not say whether it was compatable with any other OS.  

I might be making a trip to Circuit City later =D

But anyway i will go get the results of that for you.
See you in 15 min.

---

### Post by coolbian57 on 2006-09-28
```
ï»¿eth0      Link encap:Ethernet  HWaddr 00:0E:A6:D1:47:08
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1556 (1.5 KiB)  TX bytes:1556 (1.5 KiB)
```

---

### Post by coolbian57 on 2006-09-28
Thats what i got from IFconfig

---

### Post by llamakc on 2006-09-28
If at any point during this you already know what I'm saying, please say so. 

From the output of lspci and ifconfig we know that your onboard WIRED ethernet adaptor (known as eth0) is picked up and would work just fine if you plugged into a router (or cable modem).

I have two questions that you may have answered already:

1. Where is the physical location of your wireless card (builtin, PCI card, USB, PCMCIA)?

2. Was it plugged in (or properly fitted) when you ran those commands?

Many cards that are Windows-only can often work just fine with Ndiswrapper, which is not difficult to install/config. What we need to know are the answers to the above.

---

