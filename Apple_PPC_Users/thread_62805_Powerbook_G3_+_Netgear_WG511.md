---
title: "Powerbook G3 + Netgear WG511"
date: 2005-09-05
forum: Apple PPC Users
---

### Post by jarnold_ubuntu on 2005-09-05
Hi all,

I've got a Powerbook G3 (Lombard) with a Netgear WG511 PCMCIA wireless card.
I have read a bunch about various versions of the card; the v1 and v2 cards
built in Taiwan work; the China-made v3 card doesn't.  The bottom of my card
states FCC ID: PY3WG511-F v2.0 Made in Taiwan.
The card detects as a prism54 card and uploads the firmware.  The only
problem is that when I do an iwconfig on the device, I see the following:

eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It lets me set an essid, but doesn't detect any networks or do anything
useful.  Here's some more relevant information:

jase@valinor: ~> cardctl status
Socket 0:
  3.3V CardBus card
  function 0: [ready]
jase@valinor: ~> cardctl info
PRODID_1="Intersil"
PRODID_2="ISL3890"
PRODID_3="-"
PRODID_4="-"
MANFID=000b,3890
FUNCID=254

/var/log/messages:
Sep  4 23:28:07 localhost kernel: Loaded prism54 driver, version 1.2

When I eject and re-insert the card, I get the following in my dmesg:

eth1: hot unplug detected
eth1: removing device
divert: freeing divert_blk for eth1
PCI: Enabling device 0000:01:00.0 (0000 -> 0002)
divert: allocating divert_blk for eth1

lspci -v:
0000:01:00.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)
        Subsystem: Netgear: Unknown device 4800
        Flags: bus master, medium devsel, latency 80, IRQ 22
        Memory at 80000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [dc] Power Management version 1

lspci -n:
0000:01:00.0 0280: 1260:3890 (rev 01)

When I sleep the machine and it wakes back up, hotplug re-uploads the firmware
and I get this in my dmesg:

eth1: got resume request
eth1: resetting device...
eth1: uploading firmware...
eth1: firmware version: 1.0.4.3
eth1: firmware upload complete
eth1: no 'reset complete' IRQ seen - retrying
eth1: no 'reset complete' IRQ seen - retrying
eth1: interface reset failure
prism54: Your card/socket may be faulty, or IRQ line too busy :(

Anyone have any ideas why I get the NOT READY! and nothing works?  And does anyone think I should cross-post to the general hardware support forum?  Thanks!

-Jason

---

