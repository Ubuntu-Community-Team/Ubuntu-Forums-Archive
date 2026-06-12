---
title: "Serial IO help..."
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by frith on 2007-09-19
So I'm trying to get the stylus to work on my toshiba m200 tablet. It worked once before, but it doesn't now...

In my travels, I have discovered the setserial command, the dmesg command, and a few others. So here is some info:

/dev/ttyS0 exists (meaning it shows up when I do ls), as does /dev/input/wacom

Some more commands and their results:
[FONT="Courier New"]
> sudo setserial -g /dev/input/wacom 
/dev/input/wacom, UART: 16550A, Port: 0x0338, IRQ: 4

> dmesg | grep ttyS0
00:09: ttyS0 at I/O 0x338 (irq = 4) is a 16550A
ttyS0: LSR safety check engaged! [repeat this line 17 times]

> sudo cat /dev/input/wacom
cat: /dev/input/wacom: Input/output error

> sudo wacdump /dev/input/wacom
WacomOpenTablet: Invalid argument

> sudo cat /dev/ttyS0
cat: /dev/ttyS0: Input/output error

> sudo wacdump /dev/ttyS0
WacomOpenTablet: Invalid argument[/FONT]

Someone out there must be able to help me with this. A friend of mine had a quick look and said he thought the problem might be the serial driver not conversing correctly with the hardware. It works fine in windowsXP.

I really want to work this out - I want to like this OS so much, but its acting like a yuppie - treat 'em mean to keep em keen. :)

Frith.

---

