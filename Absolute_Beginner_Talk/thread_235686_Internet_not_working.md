---
title: "Internet not working?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by madman1611 on 2006-08-13
I'm trying to access the internet from my Ubuntu Live CD but I keep on getting the error: "server not found" in Mozilla Firefox. Although, I am able to access the net in Windows.

---

### Post by kb3hkg on 2006-08-13
in a terminal type ifconfig and post its output here.

Is this a wireless or wired connection?

---

### Post by OffHand on 2006-08-13
type 'lspci' in the terminal and post the output here.

```
lspci
```

---

### Post by madman1611 on 2006-08-13
Here's the output after typing ifconfig in terminal: 
Link encap: 127.0.0.1  Mask: 25.0.0.0 
inter addr: ::1/128  Scope: Host UP LOOPBACK RUNNING MTU:16436 METRIC: 1
RX packets: 167  errors: 0  dropped: 0  overruns: 0  carrier: 0
collisions: 0  txquelen: 0
RX bytes: 1198 (11.7 KiB) TX bytes: 11988 (11.7 KiB)

---

### Post by OffHand on 2006-08-13
> **madman1611 said:**
> Here's the output after typing ifconfig in terminal: 
Link encap: 127.0.0.1  Mask: 25.0.0.0 
inter addr: ::1/128  Scope: Host UP LOOPBACK RUNNING MTU:16436 METRIC: 1
RX packets: 167  errors: 0  dropped: 0  overruns: 0  carrier: 0
collisions: 0  txquelen: 0
RX bytes: 1198 (11.7 KiB) TX bytes: 11988 (11.7 KiB)

I don't see a mac address. Most isp use the mac address of the ethernetcard to identify their clients on the network. Please post the output of lspci.

edit: actually that isn't even your networkcard

---

### Post by chaudhary.akshay88 on 2006-08-13
0000:00:00.0 Host bridge :Intel corporation 440BX/ZX/DX-82443BX/ZX/DX  Host bridge(rev 03)
0000:00:00.0 Pci bridgee :Intel corporation 440BX/ZX/DX-82443BX/ZX/DX  AGP bridge(rev 03)
0000:00:03.0 Card Bus bridge : Texas Instruments PCI1225(rev 01)
0000:00:03.1 Card Bus bridge : Texas Instruments PCI1225(rev 01)
0000:00:07.0 Bridge : Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 02)
0000:00:07.1 IDE interface : Intel corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB controller : Intel corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge : Intel corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:08.0 Multimedia audio controller : ESS Technology ESI 9835 Maestro-3i PCI Audio Accelerator (rev 10)
0000:01:00.0 UGH compatible controller : ATI technologies Inc Rsge Mobility PIM AGP 2X (rev 04)

---

### Post by madman1611 on 2006-08-13
^^^ Here's the output after typing lspci in terminal. ^^^

PS. Someone I know posted it for me, therefore the username is different.

---

### Post by OffHand on 2006-08-13
I think your networkcard is not recognized by Ubuntu.
In XP r-mouse on your computer icon and choose properties. Go to the tab hardware, start device manager and tell us what you see under network adapter.

---

### Post by chaudhary.akshay88 on 2006-08-13
SpeedStreem  Ethernet USB Adapter #6

---

### Post by OffHand on 2006-08-13
If it is not recognized it will be a pain to get it working if at all.
Your best bet would be to buy a pci networkcard. They are pretty cheap.
Minde is a Realtek RTL-8139/8139C/8139C+ It works out of the box. Most Realteks do I think.

---

