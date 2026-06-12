---
title: "my usb stick doesnt work"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Felix Ruiz de Arcaute on 2006-08-08
hy
i am have installed ubuntu, and i am kind of new to linux. 
Works well, but my my usb stick doesn't work and neither does my digital camera. 
What do i have to do?

THX

:confused:

---

### Post by jordilin on 2006-08-08
It's weird, since Ubuntu detects all plugable devices automatically. Plug your usb stick and type:
```
dmesg
```
tell us, then what it says.

---

### Post by Felix Ruiz de Arcaute on 2006-08-08
eeeuhh.... do i have to copy paste everything from the terminal?
-laptop:~$ dmesg
[17179880.404000] usb 4-3: new high speed USB device using ehci_hcd and address 2
[17179881.404000] ehci_hcd 0000:00:10.3: Unlink after no-IRQ?  Controller is pro bably using the wrong IRQ.
[17179891.948000] usb 4-3: device not accepting address 2, error -110
[17179892.060000] usb 4-3: new high speed USB device using ehci_hcd and address 3
[17179903.604000] usb 4-3: device not accepting address 3, error -110
[17179903.716000] usb 4-3: new high speed USB device using ehci_hcd and address 4
[17179914.140000] usb 4-3: device not accepting address 4, error -110
[17179914.252000] usb 4-3: new high speed USB device using ehci_hcd and address 5
[17179924.676000] usb 4-3: device not accepting address 5, error -110

---

### Post by jordilin on 2006-08-08
> [17179880.404000] usb 4-3: new high speed USB device using ehci_hcd and address 2
[17179881.404000] ehci_hcd 0000:00:10.3: Unlink after no-IRQ? Controller is pro bably using the wrong IRQ.
[17179891.948000] usb 4-3: device not accepting address 2, error -110
[17179892.060000] usb 4-3: new high speed USB device using ehci_hcd and address 3
[17179903.604000] usb 4-3: device not accepting address 3, error -110
[17179903.716000] usb 4-3: new high speed USB device using ehci_hcd and address 4
[17179914.140000] usb 4-3: device not accepting address 4, error -110
[17179914.252000] usb 4-3: new high speed USB device using ehci_hcd and address 5
[17179924.676000] usb 4-3: device not accepting address 5, error -110
It seems, it's not able to detect it. What kind of filesystem format has your pendrive? fat, ntfs?

PD. Please edit the last post and make it a little bit short. only the lines pointed out by usb are valid

---

