---
title: "RAMDISK Problem Preventing a Netboot Install"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by tl3000 on 2007-04-12
I have been unable to boot or install via the Edgy LiveCDs on a Dell Dimension V400 desktop PC (PII-400MHz, 320MB ram, and 9GB HD) via the CD-ROM drive.  After a week of debugging and trying various options, no luck so I'm now trying to install manually via Windows using the netboot approach.  I have been able to initiate the install process with:

loadlin linux initrd=initrd.gz vga=normal ramdisk_size=16417 root=/dev/ram rw --

However, the startup process fails at the following screen display log messages:

[...] ...
[...] RAMDISK: Compressed image found at block 0
[...] RAMDISK: incomplete write (1024 != 32768) 16809984
[...] RAMDISK: ran out of compressed data
[...] invalid compressed format (err=1)
[...] No filesystem could mount root, tried: cramfs
[...] Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)
_

System is now hung with a blinking underscore cursor on the display screen.  A hard reset is necessary to reboot the PC.  I tried many different ramdisk_size values, and nothing seems to work.  The closest I got was with ramdisk_size=16447 which produced (31744 != 32768).  Then with ramdisk_size=16448, the log shows (-28 != 32768).  The system keeps getting hung up at this installation point.  Any solution, suggestion or advice would be greatly appreciated.

---

