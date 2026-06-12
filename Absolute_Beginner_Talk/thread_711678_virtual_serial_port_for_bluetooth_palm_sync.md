---
title: "virtual serial port for bluetooth palm sync"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by sean42 on 2008-02-29
I have a new palm centro. I am trying to sync with evolution via bluetooth.  I can transfer files to and from my phone, but I have been unable to set up hotsync.  in the in phone setup it asks for a virtual serial port.  How do I get one?

---

### Post by vgrisham on 2008-04-22
I too would love some help with this. My Palm Centro sees my Ubuntu Desktop via Bluetooth and it (the Centro) then instructs me that if I wish to sync via bluetooth, I must set up a virtual serial port. 

From the bluetooth portion of dmesg, I get: 
> 
[   52.707302] Bluetooth: Core ver 2.11
[   52.707372] NET: Registered protocol family 31
[   52.707373] Bluetooth: HCI device and connection manager initialized
[   52.707377] Bluetooth: HCI socket layer initialized
[   52.735029] Bluetooth: L2CAP ver 2.9
[   52.735033] Bluetooth: L2CAP socket layer initialized
[   52.745703] Bluetooth: RFCOMM socket layer initialized
[   52.745718] Bluetooth: RFCOMM TTY layer initialized
[   52.745719] Bluetooth: RFCOMM ver 1.8
[   54.720858] eth0: no IPv6 routers present
[   77.500529] usb 1-9: new full speed USB device using ohci_hcd and address 3
[   77.601240] usb 1-9: configuration #1 chosen from 1 choice
[   77.661062] Bluetooth: HCI USB driver ver 2.9
[   77.663536] usbcore: registered new interface driver hci_usb
[  194.563141] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[  194.563145] Bluetooth: BNEP filters: protocol multicast
[  194.584918] Bridge firewalling registered
[  194.586015] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.


Can I use this info to create a virtual serial port? If so, how please?

---

