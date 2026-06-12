---
title: "External FireWire drive not mounting"
date: 2007-06-07
forum: Apple Intel Users
---

### Post by RobinTibbs on 2007-06-07
I have encountered something odd when plugging in my Lacie firewire hard drive. now, when I plug it in, I get a little popup dialog asking what I want to do (import photos from it, do nothing etc) so Ubuntu obviously realises it's there but doesnt know what to do with it.

i have installed hfs utils but still nothing, here is the dmesg output, maybe it will help

```
[ 9002.740000] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 9002.740000] ieee1394: The root node is not cycle master capable; selecting a                                                            new root node and resetting...
[ 9003.012000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0016cbfffed5f018]
[ 9010.392000] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 9010.392000] ieee1394: The root node is not cycle master capable; selecting a                                                            new root node and resetting...
[ 9010.664000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00d04b651007c55d]
[ 9010.664000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 9010.668000] scsi4 : SBP-2 IEEE-1394

```

---

