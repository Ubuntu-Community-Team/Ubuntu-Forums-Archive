---
title: "totally LOST! Realtek RTL8139 issues"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Bosox3 on 2008-02-05
ok..Ive read the pages of these issues from here and on google but Im still Lost.
Im new to the Ubuntu linux scene and dont really get how things work just yet.

Right now I have issues w/ getting the internet to work.

Im just wondering if this issue will go away if I make my computer dual boot into XP as well.
If I get all the drivers set on the XP side..will this coincide w/ the Ubuntu part?

---

### Post by emarkd on 2008-02-05
I can't help you with that particular card, but the answer to you second question is definitely 'no'.  The two installations are completely separate and don't effect each other.

---

### Post by Bosox3 on 2008-02-05
yea, thats what I thougt. :(

---

### Post by emarkd on 2008-02-05
A google search shows that card having good support under Linux.  Are you sure that's the chipset?  Check

```
lspci
```

if you want to be sure.

---

### Post by Bosox3 on 2008-02-06
jay@jay-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
03:02.0 Communication controller: Conexant HSF 56k Data/Fax Modem

---

### Post by emarkd on 2008-02-06
Ah, see there you've actually got a card with a RTL8101E chipset.  You may have been reading the wrong advice...

Hopefully that will put you on a more useful path.

---

