---
title: "Maybe this should have been in the networking forum?"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by Reaped In Half on 2005-11-23
I just bought a D-Link DWL-650 (I have no clue what rev it is) and have tried just about everything to get it going.  I got ndiswrapper and have tried a few different xp drivers and it wont even recognize the hardware (while the drivers install ok).  iwconfig also gives me nothing... is the card dead, or am I overlooking something? 

Please dumb down your answers for me. thanks.

edit: by the way, I'm using breezy.

---

### Post by towsonu2003 on 2005-11-24
first ```
 sudo modprobe ndiswrapper
``` then posting output for
```

sudo iwconfig
sudo ifconfig
```
may help.

---

### Post by Reaped In Half on 2005-11-25
are either of those solutions going to help if the card won't even get recognized by the computer?

---

### Post by wsanders on 2005-11-25
Ndiswrapper has to be inserted into modprobe in order for the computer to recognize the drivers. If you haven't tried sudo modprobe ndiswrapper before then that's likely why your computer hasn't recognized it. First try that, then display the output of ifconfig.

---

### Post by Reaped In Half on 2005-11-26
Ouch... Here's the output.

FATAL: Error inserting ndiswrapper 

(/lib/modules/2.6.12-10-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Oh, and I know the card isn't dead.  Itested it today on my friend's XP laptop... I refuse to go back to windows, and would really hate to switch distros.

thanks for your help by the way.

---

### Post by akiro.yamamoto on 2005-11-26
Reaped,
Try using 
                 sudo modprobe ndiswrapper
The error you reported only happens if you don't have permission to insert the module into the running process stream. Therefore SUDO is needed to insert the module. 
Regards

---

### Post by Reaped In Half on 2005-11-26
Yea, that's the thing... You'd think by the output given, that I didn't use "sudo".  I'm not sure what the deal is.

james@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:992678 (969.4 KiB)  TX bytes:992678 (969.4 KiB)

that's ifconfig's output.  
Also, it's definitely not an issue with PCMCIA drivers... My Xircom 10/100 Ethernet card works fine, and does an old external CD-rom.

---

### Post by Reaped In Half on 2005-11-26
lo        no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

and the output of iwconfig...

---

### Post by akiro.yamamoto on 2005-11-26
Reaped,
Can you post the output of 
lspci -v
It may help in tracking this problem. At least it should give you a starting point.
This is mostly a check that the system is seeing the card.
The -v switch is to provide more detailed info.
If the system is seeing the card then you know it's a sofware problem and can google or check back here for help with the card that your using.

---

### Post by Reaped In Half on 2005-11-26
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Subsystem: Toshiba America Info Systems Toshiba Tecra 8100 Laptop System Chipset
        Flags: bus master, medium devsel, latency 64
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: fec00000-ff7fffff

0000:00:05.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:05.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at fff0 [size=16]

0000:00:05.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at ff80 [size=32]

0000:00:05.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
        Flags: medium devsel, IRQ 9

0000:00:07.0 Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
        Subsystem: Toshiba America Info Systems Internal V.90 Modem
        Flags: bus master, medium devsel, latency 0, IRQ 3
        Memory at ffefff00 (32-bit, non-prefetchable) [size=256]
        I/O ports at 02f8 [size=8]
        I/O ports at 1c00 [size=256]
        Capabilities: <available only to root>

0000:00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
        Subsystem: Toshiba America Info Systems FIR Port Type-DO
        Flags: bus master, slow devsel, latency 64, IRQ 11
        I/O ports at ff60 [size=32]
        Capabilities: <available only to root>

0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, slow devsel, latency 168, IRQ 11
        Memory at 10100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
        Memory window 0: 10400000-107ff000 (prefetchable)
        Memory window 1: 10800000-10bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, slow devsel, latency 168, IRQ 11
        Memory at 10101000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=0
        Memory window 0: 10c00000-10fff000 (prefetchable)
        Memory window 1: 11000000-113ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:00:0c.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
        Subsystem: Toshiba America Info Systems ES1978 Maestro-2E Audiodrive
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at fc00 [size=256]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: Trident Microsystems Cyber 9540 (rev 52) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, 66MHz, medium devsel, latency 8, IRQ 11
        Memory at ff400000 (32-bit, non-prefetchable) [size=4M]
        Memory at ff3e0000 (32-bit, non-prefetchable) [size=128K]
        Memory at fec00000 (32-bit, non-prefetchable) [size=4M]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
        Subsystem: D-Link System Inc: Unknown device 3302
        Flags: medium devsel, IRQ 11
        I/O ports at 4000 [disabled] [size=256]
        Memory at 10800000 (32-bit, non-prefetchable) [disabled] [size=512]
        Capabilities: <available only to root>


Well that almost looks promising... Thanks again for your help.

---

### Post by akiro.yamamoto on 2005-11-26
Reaped,
Here are a couple of links that might be of help....
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)
[http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)
[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

---

