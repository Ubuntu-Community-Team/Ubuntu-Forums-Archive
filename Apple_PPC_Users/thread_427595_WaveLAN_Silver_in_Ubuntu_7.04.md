---
title: "WaveLAN Silver in Ubuntu 7.04"
date: 2007-04-29
forum: Apple PPC Users
---

### Post by john8520 on 2007-04-29
Hi,
I just installed (then updated) Fiesty on my powerbook lombard, and to my supprise everything went prefectly, I didn't have any little snags, and there is even audio and battery support! It runs pretty snappily too, which is nice for a 333MHz machine.

Anyways, I have a Lucent WaveLAN silver card that I'd like to use in it. The card worked in OS X/9, but in fiesty when I run lspci, I see things like the usb controler, video controler, and the cardbus controler, but no card! A friend of mine told be that I needed to get something called 'cardctl', so I apt-got it, and ran it (then ran cardctl info) and it spit back 'no pcmcia drive in /proc/devices'. So, my question is, can I get this driver anywhere? Googling doesn't seem to help.

Thanks!
John

---

### Post by john8520 on 2007-05-01
Anybody? I've been all over the web looking for info on this, but I can't find anything!

---

### Post by jwbaker on 2007-05-02
cardctl is obsolete.  Install pcmciautils (should already be installed by default) and use pccardctl.  I have a WaveLAN Gold and a Pismo, I'll try it out tomorrow and report here.  Good luck.

---

### Post by john8520 on 2007-05-02
Alright, I ran pccardctl (it was already installed) and did ls, info, and ident, and it doesn't even see the card at all. 

I also tried popping my Belkin USB 2 card (USB 1.1 when the PSU isn't connected) and rebooting while its in, but still its not noticed.

I have verified that both these cards operate in this machin in OS X and OS 9 perfectly (I have a second hard, and I swap between the two).

---

### Post by jwbaker on 2007-05-02
It works perfectly with a WaveLAN Gold on my Pismo running 7.04.  I would check to make sure that the yenta_socket kernel module is loaded (lsmod | grep yenta_socket) and if not, load it manually (modprobe -a yenta_socket).

```

jwb@pismo:~$ lspcmcia 
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0001:10:1a.0)
Socket 0 Device 0:      [orinoco_cs]            (bus ID: 0.0)
jwb@pismo:~$ pccardctl ident
Socket 0:
  product info: "Lucent Technologies", "WaveLAN/IEEE", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)

```
from dmesg:

```

[ 6367.479723] pccard: PCMCIA card inserted into slot 0
[ 6367.479761] cs: memory probe 0x80000000-0xafffffff: excluding 0x80000000-0x807fffff 0x90000000-0xa07fffff
[ 6367.508627] cs: memory probe 0xf3000000-0xf3ffffff: excluding 0xf3000000-0xf33fffff
[ 6367.514469] pcmcia: registering new device pcmcia0.0
[ 6367.833837] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[ 6367.841753] pcmcia: request for exclusive IRQ could not be fulfilled.
[ 6367.841777] pcmcia: the driver needs updating to supported shared IRQ lines.
[ 6367.922790] eth2: Hardware identity 0001:0001:0004:0000
[ 6367.922909] eth2: Station identity  001f:0001:0006:0006
[ 6367.922923] eth2: Firmware determined as Lucent/Agere 6.06
[ 6367.922932] eth2: Ad-hoc demo mode supported
[ 6367.922942] eth2: IEEE standard IBSS ad-hoc mode supported
[ 6367.922951] eth2: WEP supported, 104-bit key
[ 6367.923031] eth2: MAC address 00:02:2D:0C:91:3A
[ 6367.923123] eth2: Station name "HERMES I"
[ 6367.923647] eth2: ready
[ 6367.929802] eth2: orinoco_cs at 0.0, irq 58, io 0x0000-0x003f

```

---

### Post by john8520 on 2007-05-02
Yup, yenta_socket is loaded. It just doesn't see the card at all for some reason...

I have another PCMCIA wifi card laying around, I'll test it.

---

### Post by gvigorus on 2007-09-19
Hi. Same issue here i.e. PPC Lombard with Feisty and WaveLan Silver. Has anyone figured this one out?!?!

---

