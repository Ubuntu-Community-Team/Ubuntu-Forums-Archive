---
title: "Wireless Problems"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by aerowrestlerisu on 2005-10-04
Hi, I just recently purchaced a Dell Inspiron 6000. I needed it for school work and decided to make it dual bootable with XP and ubuntu 5.04.
Anyway, when I first installed ubuntu, the wireless worked fine. I tried detecting another network on campus, and that didn't work. The problem is that now I can't seem to get the wireless to work anywhere. I didn't change any settings, so I don't know what I did.
Could somebody please give me a hand?

---

### Post by fabiand on 2005-10-06
Hey,

open a terminal and do:
sudo iwconfig
sudo iwlist eth0 scan

and send thos informations back here

- fabiand

---

### Post by aerowrestlerisu on 2005-10-06
Okay, this is weird. The  wireless has decided to work at home again. I guess all I need now is help picking up the school's network when I am on campus. Here is that stuff though:

sudo iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"TehRouter"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:30:BD:C3:BE:A2
          Bit Rate=11 Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:54C4-3775-66C2-7FC5-49CC-051A-1C   Security mode:open
          Power Management:off
          Link Quality=62/100  Signal level=-63 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2

sit0      no wireless extensions.

sudo iwlist etho0 scan

eth0            Interface doesn't support scanning.


My wireless card is assigned to eth1. At least I think so. If that has any bearing on what is going on.

---

