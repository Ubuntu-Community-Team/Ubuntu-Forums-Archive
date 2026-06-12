---
title: "Trouble with Eee PC 1001PX"
date: 2012-03-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by U-95 on 2012-03-01
Greetings. I own an Eee PC 1001PX that had Windows 7 Starter replaced with Ubuntu Oneiric Ocelot running Xfce. Everything went fine until a few hours ago, when running on battery power and attempting to open the personal directory with Thunar got a total crash -even the touchpad did not respond-.

After some tests, I got this with dmesg. This happens when I plug in the AC adaptor:

[ 1930.721964] keyboard: can't emulate rawmode for keycode 240
[ 1930.722010] keyboard: can't emulate rawmode for keycode 240
[ 1930.722032] asus_wmi: Unknown key 58 pressed
[ 1932.468988] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0

When it's unplugged:

[ 2064.852183] keyboard: can't emulate rawmode for keycode 240
[ 2064.852219] keyboard: can't emulate rawmode for keycode 240
[ 2064.852240] asus_wmi: Unknown key 57 pressed
[ 2066.995228] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600

In both cases, I get this sometimes after the re-mounting of sda1:

[ 2125.817735] ata1: exception Emask 0x40 SAct 0x0 SErr 0xc0800 action 0x7
[ 2125.817760] ata1: SError: { HostInt CommWake 10B8B }
[ 2125.817786] ata1: hard resetting link
[ 2126.136096] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2126.137814] ata1.00: unexpected _GTF length (8)
[ 2126.139998] ata1.00: unexpected _GTF length (8)
[ 2126.140360] ata1.00: configured for UDMA/133
[ 2126.156099] ata1: EH complete

This appears -sometimes- during startup:

[    1.405404] atl1c 0000:01:00.0: version 1.0.1.0-NAPI
[    1.668090] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.669370] ata1.00: unexpected _GTF length (8)
[    1.669657] ata1.00: ATA-8: WDC WD2500BEVT-80A23T0, 01.01A01, max UDMA/133
[    1.669673] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.670983] ata1.00: unexpected _GTF length (8)
[    1.671267] ata1.00: configured for UDMA/133

And sometimes this appears instead:

[  507.546618] ata1.00: exception Emask 0x50 SAct 0x6 SErr 0x2c0900 action 0x6 f
rozen
[  507.546638] ata1.00: irq_stat 0x08000000, interface fatal error
[  507.546656] ata1: SError: { UnrecovData HostInt CommWake 10B8B BadCRC }
[  507.546673] ata1.00: failed command: READ FPDMA QUEUED
[  507.546706] ata1.00: cmd 60/00:08:10:dd:eb/04:00:01:00:00/40 tag 1 ncq 524288
 in
[  507.546714]          res 40/00:14:10:e1:eb/00:00:01:00:00/40 Emask 0x50 (ATA 
bus error)
[  507.546732] ata1.00: status: { DRDY }
[  507.546747] ata1.00: failed command: READ FPDMA QUEUED
[  507.546781] ata1.00: cmd 60/00:10:10:e1:eb/04:00:01:00:00/40 tag 2 ncq 524288
 in
[  507.546789]          res 40/00:14:10:e1:eb/00:00:01:00:00/40 Emask 0x50 (ATA 
bus error)
[  507.546806] ata1.00: status: { DRDY }
[  507.546831] ata1: hard resetting link
[  508.996093] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  509.036690] ata1.00: unexpected _GTF length (8)
[  509.038889] ata1.00: unexpected _GTF length (8)
[  509.039269] ata1.00: configured for UDMA/133
[  509.039534] ata1: EH complete

Other times, when unplugging the computer freezes with the disk light turned on and this appears on dmesg:

[ 2390.112104] ata1.00: exception Emask 0x40 SAct 0x7 SErr 0x8c0800 action 0x6 frozen
[ 2390.112123] ata1: SError: { HostInt CommWake 10B8B LinkSeq }
[ 2390.112136] ata1.00: failed command: WRITE FPDMA QUEUED
[ 2390.112161] ata1.00: cmd 61/08:00:70:43:7c/00:00:0d:00:00/40 tag 0 ncq 4096 out
[ 2390.112166]          res 40/00:00:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 2390.112177] ata1.00: status: { DRDY }
[ 2390.112187] ata1.00: failed command: WRITE FPDMA QUEUED
[ 2390.112211] ata1.00: cmd 61/08:08:e0:88:04/00:00:00:00:00/40 tag 1 ncq 4096 out
[ 2390.112216]          res 40/00:14:10:e1:eb/00:00:01:00:00/40 Emask 0x44 (timeout)
[ 2390.112227] ata1.00: status: { DRDY }
[ 2390.112237] ata1.00: failed command: WRITE FPDMA QUEUED
[ 2390.112260] ata1.00: cmd 61/98:10:18:e3:44/00:00:0e:00:00/40 tag 2 ncq 77824 out
[ 2390.112265]          res 40/00:14:10:e1:eb/00:00:01:00:00/40 Emask 0x44 (timeout)
[ 2390.112276] ata1.00: status: { DRDY }
[ 2390.112292] ata1: hard resetting link
[ 2390.432087] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2390.433572] ata1.00: unexpected _GTF length (8)
[ 2390.435482] ata1.00: unexpected _GTF length (8)
[ 2390.435791] ata1.00: configured for UDMA/133
[ 2390.435929] ata1.00: device reported invalid CHS sector 0
[ 2390.435960] ata1: EH complete
[ 2392.576784] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0


¿Any ideas?. The disk seems to be fine -the utility to check disks find no errors as well as the automatic check Ubuntu makes after certain number of startups-.

**EDIT. **There're no sounds that could indicate the disk is going to fall. In fact, when it's plugged it works fine and most of the errors seems to come when I'm running on battery. Also, forgot to comment I'm using Jupiter as power manager.

---

### Post by Lokireloaded on 2012-03-01
This is going to sound pathetic, but here goes.
Have you tried booting from the bootstick?
also you could try a fresh install.
Thats pretty much what I would do (and in that order).

Edit: I posted this as I pretty much am in the same situation. Same model and whatnot. And I did also switch from 7 starter to ubuntu 11.10

---

