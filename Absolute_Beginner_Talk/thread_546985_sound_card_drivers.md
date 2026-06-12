---
title: "sound card drivers"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by alcopete on 2007-09-09
once again ive run head first into a brick wall and need some help here. im trying to get my intergrated sound card working. the motherboard is a foxconn  RC4107MA-RS2. ive run 'esd' in a terminal and got the following message:
ALSA lib confmisc.c:670: (snd_func_card_driver) cannot find card '0'.
can anybody help out here or know where i can get drivers for it as the ones on the foxconnchannel  are all windows based. 
thanks in advance

---

### Post by overdrank on 2007-09-09
> **alcopete said:**
> once again ive run head first into a brick wall and need some help here. im trying to get my intergrated sound card working. the motherboard is a foxconn  RC4107MA-RS2. ive run 'esd' in a terminal and got the following message:
ALSA lib confmisc.c:670: (snd_func_card_driver) cannot find card '0'.
can anybody help out here or know where i can get drivers for it as the ones on the foxconnchannel  are all windows based. 
thanks in advance

Hi can you post the output of the command in the terminal
```
lspci
```

---

### Post by alcopete on 2007-09-09
pci bridge:  rs480 pci bridge
ide interface: ati 437a serial ata controller
ide interface: ati 4379 serial ata controller
usb controller: ixp sb400 
host bridge: radeon xpress 200 
isa bridge: ixp sb400 pci-isa bridge
pci  bridge: ixp sb400 pci-pci bridge
ide interface: std dual channel pci ide controller
multimedia audio controller: ixp sb400 ac'97 audio controller

from motherboard specifications:
Core Logic (Chipset)
ATI Radeon Xpress 200 (RC410 + SB450)
Audio Chipset
The motherboard features integrated sound and network capabilities:
Sound: Realtek AC97 5.1 channel
Network: Realtek 8100C Fast Ethernet (10/100) controller

---

### Post by overdrank on 2007-09-09
[QUOTE=alcopete;3337190]pci bridge:  rs480 pci bridge
ide interface: ati 437a serial ata controller
ide interface: ati 4379 serial ata controller
usb controller: ixp sb400 
host bridge: radeon xpress 200 
isa bridge: ixp sb400 pci-isa bridge
pci  bridge: ixp sb400 pci-pci bridge
ide interface: std dual channel pci ide controller
[COLOR="Red"]multimedia audio controller: ixp sb400 ac'97 audio controller[[/COLOR]/QUOTE]

Ok a quick search leads here
[http://ubuntuforums.org/showthread.php?t=251123&highlight=sb400+ac%2797+audio+controller](http://ubuntuforums.org/showthread.php?t=251123&highlight=sb400+ac%2797+audio+controller)
Good luck and hope this helps!

---

### Post by apparle on 2007-09-13
Hi there
I also have the same motherboard and trying to get the sound card working.
I am new to linux and unable to understand the how to apply the patch on the given link

---

