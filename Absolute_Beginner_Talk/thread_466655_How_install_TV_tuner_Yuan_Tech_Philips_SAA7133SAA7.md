---
title: "How install TV tuner Yuan Tech Philips SAA7133/SAA7135"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by jcombalicer on 2007-06-06
Hi! I'm new to Linux.

Can someone here help me how to Play TV in step by step guide.

My TV tuner doesnt work well with sabayon or ubuntu, but i can see it in lspci. how can i activate this device.

Please tell me the instruction in step by step guide.

Thank you!

[B]Philips saa7133/saa7135
Yuan Yuan Tech Purple TV[/B]


**Yuan FUNTV TUN900 PCI-FM**

chips: saa7135hl/101, 24c02n, 74hc4053d, em78p153sn, xtal N6.000,  xtal N32.110 3B20PA
tuner: tda8275, tda8290
connectors: radio (mini klinke), audio out, rm (mini klinke), ant-in, S-in (=S-Video), Audio in
pcb: TUN-900 Rev:1.4
remote control: smartVDO
software: FUNTV, Cyberlink PowerCinema3

pci-id: 1131:7133
subsystem id: 12ab:0800

saa7133[0]: subsystem: 12ab:0800, board: Yuan TUN-900 (saa7135) [card=66,insmod option]
saa7133[0]: board init: gpio is 0
saa7133[0]: i2c eeprom 00: ab 12 00 08 00 00 00 00 00 00 00 00 00 00 00 00
saa7133[0]: i2c eeprom 10: ff ff ff ff 15 00 05 01 13 c2 db ff ff ff ff ff
saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

---

### Post by josesanders on 2007-06-07
I'm not sure if it will work, but you can try my howto for the saa7134:

[http://ubuntuforums.org/showthread.php?t=408654](http://ubuntuforums.org/showthread.php?t=408654)

---

