---
title: "dmesg question"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by bountonw on 2006-02-09
I should probably just stick to one tutorial, but I am working my way through several and learning everyday.  The current tutorial "Getting Started with Linux"

[http://www.linuxgazette.com/issue35/advani.html](http://www.linuxgazette.com/issue35/advani.html)

beins with explaining the dmesg command and asking me to do it.
When I try, I get the following.

> ton@wmien01:~$ dmesg
 key released (translated set 2, code 0xaa on isa0060/serio0).
[4310939.231000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310939.293000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310939.293000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310939.382000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310939.382000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310939.451000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310939.451000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310939.689000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310939.689000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310939.822000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310939.822000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310939.974000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310939.974000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310940.075000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310940.075000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310940.290000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310940.290000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310940.379000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310940.379000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310958.238000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310958.238000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310958.328000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310958.328000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310958.621000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310958.621000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310958.710000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310958.710000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310971.967000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310971.967000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310972.084000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310972.084000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310982.069000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310982.069000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310982.162000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310982.162000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311393.182000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311393.182000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311393.260000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311393.260000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311465.370000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311465.370000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311465.455000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311465.455000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311469.376000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311469.376000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311469.501000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311469.501000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311469.684000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311469.684000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311469.777000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311469.777000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311530.892000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311530.892000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311530.965000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311530.965000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311531.196000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311531.196000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311531.265000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311531.265000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311531.381000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311531.381000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311531.467000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311531.467000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311531.552000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311531.552000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311531.637000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311531.637000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311531.718000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311531.718000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311531.780000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311531.780000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311532.074000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311532.074000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311532.098000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311532.098000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311532.332000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311532.332000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311532.402000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311532.402000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311532.609000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311532.609000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311532.682000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311532.682000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311539.137000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311539.137000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311539.196000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311539.196000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311539.281000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311539.281000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311539.343000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311539.343000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311539.412000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311539.412000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311539.482000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311539.482000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311539.554000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311539.554000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311539.632000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311539.632000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311539.717000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311539.717000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311539.775000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311539.775000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311539.926000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311539.926000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311540.031000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311540.031000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311587.951000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311587.951000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311588.060000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311588.060000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311588.271000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311588.271000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311588.340000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311588.340000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311661.166000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311661.166000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311661.268000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311661.268000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311805.181000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311805.181000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311805.267000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311805.267000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312157.942000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312157.942000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312158.015000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312158.015000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312158.305000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312158.305000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312158.414000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312158.414000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312158.833000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312158.833000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312158.938000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312158.938000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312262.469000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312262.469000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312262.546000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312262.546000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312262.769000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312262.769000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312262.843000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312262.843000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312268.070000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312268.070000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312268.156000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312268.156000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312268.221000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312268.221000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312268.298000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312268.298000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312268.363000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312268.363000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312268.441000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312268.441000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312268.573000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312268.573000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312268.666000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312268.666000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312268.814000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312268.814000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312268.888000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312268.888000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312284.950000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312284.950000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312285.004000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312285.004000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312285.084000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312285.084000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312285.154000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312285.154000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312285.899000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312285.899000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312285.992000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312285.992000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312286.596000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4312286.596000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312286.706000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4312286.706000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4312574.467000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[4312575.032000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04E8 pid 0x326C
[4312575.033000] usbcore: registered new driver usblp
[4312575.033000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver


This is very different from their example of which has this
> 
Serial driver version 4.13 with no serial options enabled
tty00 at 0x03f8 (irq = 4) is a 16450
tty01 at 0x02f8 (irq = 3) is a 16450
Real Time Clock Driver v1.07
hda: QUANTUM FIREBALL_TM2110A, 2014MB w/76kB Cache, CHS=1023/64/63
hdc: CREATIVECD2421E, ATAPI CDROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
ide1 at 0x170-0x177,0x376 on irq 15
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
md driver 0.35 MAX_MD_DEV=4, MAX_REAL=8
raid0 personality registered
DLCI driver v0.30, 12 Sep 1996, [email]mike.mclagan@Linux.org[/email].
Partition check:
hda: hda1 hda2 < hda5 hda6 hda7 >
VFS: Mounted root (ext2 filesystem) readonly.
Adding Swap: 16092k swap-space (priority -1)
Soundblaster audio driver Copyright (C) by Hannu Savolainen 1993-1996
SB 3.1 detected OK (220)
sb: Interrupt test on IRQ5 failed - device disabled.
YM3812 and OPL-3 driver Copyright (C) by Hannu Savolainen, Rob Hooft
1993-1996
sysctl: ip forwarding off
Swansea University Computer Society IPX 0.34 for NET3.035
IPX Portions Copyright (c) 1995 Caldera, Inc.

I am have problems with my sound card not working and I plan on hooking up my PDA eventuall etc.  Any idea what is wrong here?

---

### Post by Pragmatist on 2006-02-09
Your not alone! :)

Here is the solution:

https://wiki.ubuntu.com/'setkeycodes_e02a_%3ckeycode%3e'_issue?highlight=% 28e02a%29

---

### Post by dentament on 2006-06-15
The link above doesn't work any longer. Maybe this can help:
[http://www.ubuntuforums.org/showthread.php?t=76271&highlight=atkbd.c](http://www.ubuntuforums.org/showthread.php?t=76271&highlight=atkbd.c)

---

