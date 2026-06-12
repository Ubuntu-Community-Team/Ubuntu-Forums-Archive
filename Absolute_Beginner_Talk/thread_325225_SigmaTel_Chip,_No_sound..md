---
title: "SigmaTel Chip, No sound."
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Libere on 2006-12-25
Allo Folks, 

I'm dual booting Ubuntu 6.06 on a Sony VIAO ( RB64G ) . 
Specs here if helpful: [http://review.zdnet.com/Sony_VAIO_RB64G_Pentium_D_920_2_8_GHz/4507-3118_16-31738510.html?tag=ut](http://review.zdnet.com/Sony_VAIO_RB64G_Pentium_D_920_2_8_GHz/4507-3118_16-31738510.html?tag=ut) 

Everything is as it came, except the graphics card which was switched out for an Nvidia GeForce 7600 GT OC.  So far everything works great, I even managed to google enough to enable 3D Graphics Acceleration successfully.  Sadly, my Google-Fu is not great enough to figure out why the sound isn't working.  (It works fine in windows.)   

I typed alsamixer into terminal and got this:   
Card: HDA Intel   Chip: SigmaTel STAC7661  
Both are at 100%, but no sound from anything.

I tried to follow this guide: 
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

And I got all this:  (But my Chipset isn't listed on the ALSA Driver site.  Am I out of luck?)

kali@Shakti:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kali@Shakti:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 945G/P PCI Express Graphics Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: 54000000-55ffffff
        Prefetchable memory behind bridge: 0000000040000000-000000004ff00000
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at 56200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 56100000-561fffff
        Capabilities: <available only to root>

0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: 56300000-563fffff
        Capabilities: <available only to root>

0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: 56400000-564fffff
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at 4080 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at 4060 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 4040 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 4020 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, medium devsel, latency 0, IRQ 58
        Memory at 56204400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 56000000-560fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053f00000
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 40b0 [size=16]

0000:00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=RAID (rev 01)
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 50
        I/O ports at 40c8 [size=8]
        I/O ports at 40e4 [size=4]
        I/O ports at 40c0 [size=8]
        I/O ports at 40e0 [size=4]
        I/O ports at 40a0 [size=16]
        Memory at 56204000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: medium devsel, IRQ 11
        I/O ports at 4000 [size=32]

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0391 (rev a1) (prog-if 00 [VGA])
        Subsystem: Unknown device 19f1:201f
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at 55000000 (32-bit, non-prefetchable) [size=16M]
        Memory at 40000000 (64-bit, prefetchable) [size=256M]
        Memory at 54000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at 3000 [size=128]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at 56100000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 2000 [size=32]
        Capabilities: <available only to root>

0000:05:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Sony Corporation: Unknown device 813d
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at 50000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:05:01.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
        Subsystem: Agere Systems: Unknown device 044c
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at 56004800 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1100 [size=8]
        I/O ports at 1000 [size=256]
        Capabilities: <available only to root>

0000:05:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at 56004000 (32-bit, non-prefetchable) [size=2K]
        Memory at 56000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

Ideas, suggestions and links would be greatly appreciated.

Thanks! 
Libere

---

### Post by whyameye on 2006-12-25
[https://launchpad.net/distros/ubuntu/+source/alsa-driver/+bug/33719](https://launchpad.net/distros/ubuntu/+source/alsa-driver/+bug/33719)

---

