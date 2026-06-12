---
title: "fuzzy windows in xubuntu"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by grimdaze on 2006-05-28
I recently installed xubuntu flight 7 of dapper. This is best described with a screenshot so...
[IMG]http://img100.imageshack.us/img100/9889/screenshot9hd.png[/IMG]

The window border is all kinds of screwy.
So far this is only a problem with zsnes and any win-software that I run in wine.
Any help?

P.S. If you need graphic card info or something you'll need to give me the command or tell me where to find it because I forgot.

---

### Post by dmizer on 2006-05-28
[QUOTE=grimdaze]I recently installed xubuntu flight 7 of dapper. This is best described with a screenshot so...

P.S. If you need graphic card info or something you'll need to give me the command or tell me where to find it because I forgot.[/QUOTE]
post the output of:
```
lspci -v
```

---

### Post by grimdaze on 2006-05-28
```
grimdaze@xubuntu:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
        Subsystem: Dell: Unknown device 00b4
        Flags: bus master, fast devsel, latency 0

0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 00b4
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 9
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Memory at ff000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fd000000-feffffff
        Prefetchable memory behind bridge: 20000000-200fffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Intel Corporation 82801AA IDE
        Flags: bus master, medium devsel, latency 0
        I/O ports at ffa0 [size=16]

0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation 82801AA USB
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at ff80 [size=32]

0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
        Subsystem: Intel Corporation 82801AA SMBus
        Flags: medium devsel, IRQ 10
        I/O ports at dcd0 [size=16]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
        Subsystem: Dell: Unknown device 00b4
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at d800 [size=256]
        I/O ports at dc80 [size=64]

0000:01:0b.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04) (prog-if 00 [Generic])
        Subsystem: CastleNet Technology Inc.: Unknown device 0811
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 9
        Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ec00 [size=256]
        Capabilities: <available only to root>

0000:01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
        Subsystem: Dell: Unknown device 00b4
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at e880 [size=128]
        Memory at fdffec00 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: <available only to root>

```

Just recently got it with mupen64(n64 emulator) too, and I didn't have this problem with Breezy + Gnome.

---

### Post by dmizer on 2006-05-28
first, you'll need to know the horiz/vert refresh rates of your display.  check the manual ... back of the monitor sometimes, or the manufacture website.

then:
```
sudo dpkg-reconfigure xserver-xorg
```
this will allow you to reconfigure your display as well as keyboard settings, and video card settings.  there are lots of options, if you are unsure, just use the default selection.

when it asks you about your video card driver, scroll up and choose the 810 option, and continue on.  it will ask for display refresh rates after that.
when you are done, type this:
```
sudo /etc/init.d/gdm restart
```
see if that helps.

---

