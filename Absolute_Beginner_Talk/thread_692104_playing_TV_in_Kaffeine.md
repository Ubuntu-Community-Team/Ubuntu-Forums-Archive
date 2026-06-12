---
title: "playing TV in Kaffeine"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by stoppage on 2008-02-09
Hi. Im trying to get my TV card, a cheapo 713 model from Phillips working in &#8220;Feisty&#8221;. I decided, after fumbling around for hours looking for channels.config file to install &#8220;Kaffeine&#8221; and &#8220;Xine&#8221; player. Ive also got DVB utils installed. When I open Kaffeine I get &#8220;cant bind info socket&#8221;. Can anybody help a Newbie out here please?
p.s. If it helps, I originally wanted TV in VLC player. On a scan instruction in consol I got this....

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/de-Frankfurt > ~/Desktop/channels.conf

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/de-Frankfurt

using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'

main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

---

### Post by Drakkor on 2008-02-09
Sorry, don't know nothing about Kaffeine,but I'm using TvTime with an old Haupppauge WinTV card, and 
it works great ! :)

---

### Post by stoppage on 2008-02-09
Thanks for the support, but Ive since discovered that /dev/dvb doenst even exist on my file system! Now I'm really at a loss! Anybody?

---

### Post by ferebee on 2008-02-09
My tv card appears to be /dev/video0 - you might  try opening Device Manager under System>Preferences>Hardware Information to get info on your card's location.

Edited to add:

Other users have had difficulties with this card or cards using this chipset - you may find these two threads helpful:
This thread and this post in particular : [http://ubuntuforums.org/showpost.php?p=3037818&postcount=27](http://ubuntuforums.org/showpost.php?p=3037818&postcount=27)
or: [http://ubuntuforums.org/showthread.php?t=478973&highlight=saa7134+feisty](http://ubuntuforums.org/showthread.php?t=478973&highlight=saa7134+feisty)

---

### Post by stoppage on 2008-02-11
From the first thread, “$ grep card= /var/log/dmesg” returns “[   50.022604] saa7134[0]: subsystem: 4e42:0138, board: LifeView FlyVIDEO3000 [card=2,autodetected]”

The appropriate section of “dmesg” returns following...

50.021997] saa7130/34: v4l2 driver version 0.2.14 loaded

[   50.022581] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17

[   50.022591] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 21

[   50.022599] saa7134[0]: found at 0000:02:07.0, rev: 1, irq: 21, latency: 32, mmio: 0xfdfff000

[   50.022604] saa7134[0]: subsystem: 4e42:0138, board: LifeView FlyVIDEO3000 [card=2,autodetected]

[   50.022612] saa7134[0]: board init: gpio is 39100

[   50.022615] saa7134[0]: there are different flyvideo cards with different tuners

[   50.022616] saa7134[0]: out there, you might have to use the tuner=<nr> insmod

[   50.022618] saa7134[0]: option to override the default value.

[   50.022836] input: saa7134 IR (LifeView FlyVIDEO30 as /class/input/input3

[   50.169725] saa7134[0]: i2c eeprom 00: 42 4e 38 01 10 28 ff ff ff ff ff ff ff ff ff ff

[   50.169733] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   50.169739] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   50.169745] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   50.169751] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   50.169757] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   50.169763] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   50.169769] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   50.185711] tuner 2-0061: chip found @ 0xc2 (saa7134[0])

[   50.185749] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))

[   50.185752] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))

[   50.197675] tuner 2-0063: chip found @ 0xc6 (saa7134[0])

[   50.208927] saa7134[0]: registered device video0 [v4l2]

[   50.209047] saa7134[0]: registered device vbi0

[   50.209155] saa7134[0]: registered device radio0


As a newcomer to Linux I find a lot of this a trifle overwhelming!
But from another entry in forum Ive discovered that the “enable dvb client” can safely be disabled in “Kanotix”.
The original “can't bind info socket” message then disappears. Now, on “recive broadcast stream” (which is TV, or?) I get “sender address:local host.....port 8080” , when I choose this I get “no plugin found to handle this resource “
So do I actually unclick “enable dvb client” (and then deal with the new scenario) or not?  
And thanks for your patience!

---

