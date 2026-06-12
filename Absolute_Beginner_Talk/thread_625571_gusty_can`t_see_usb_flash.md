---
title: "gusty can`t see usb flash"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by q11q11 on 2007-11-28
Hello ALL!

I`m trying to mount usb flash (LG 1Gb), after insertion into port nothing happens, no /dev/sda, /dev/sdd or something appears

here are some outputs:

$dmesg
[ 5630.904933] usb 4-4: new high speed USB device using ehci_hcd and address 41
[ 5631.312847] usb 4-4: device not accepting address 41, error -71
[ 7436.183354] usb 4-4: new high speed USB device using ehci_hcd and address 43
[ 7437.055397] hub 4-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 7437.167196] usb 4-4: new high speed USB device using ehci_hcd and address 44
[ 7438.039267] hub 4-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 7438.150983] usb 4-4: new high speed USB device using ehci_hcd and address 45
[ 7438.558889] usb 4-4: device not accepting address 45, error -71
[ 7438.854868] usb 4-4: new high speed USB device using ehci_hcd and address 47
[ 7439.354806] usb 4-4: new high speed USB device using ehci_hcd and address 48
[ 7440.226827] hub 4-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 7440.338570] usb 4-4: new high speed USB device using ehci_hcd and address 49
[ 7441.210697] hub 4-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 7441.322387] usb 4-4: new high speed USB device using ehci_hcd and address 50
[ 7441.730291] usb 4-4: device not accepting address 50, error -71
[ 7441.842285] usb 4-4: new high speed USB device using ehci_hcd and address 51
[ 7442.250195] usb 4-4: device not accepting address 51, error -71

$ tail -f /var/log/messages
Nov 28 11:07:07 comp-desktop kernel: [ 5630.904933] usb 4-4: new high speed USB device using ehci_hcd and address 41
Nov 28 11:34:10 comp-desktop -- MARK --
Nov 28 11:37:13 comp-desktop kernel: [ 7436.183354] usb 4-4: new high speed USB device using ehci_hcd and address 43
Nov 28 11:37:14 comp-desktop kernel: [ 7437.167196] usb 4-4: new high speed USB device using ehci_hcd and address 44
Nov 28 11:37:15 comp-desktop kernel: [ 7438.150983] usb 4-4: new high speed USB device using ehci_hcd and address 45
Nov 28 11:37:15 comp-desktop kernel: [ 7438.854868] usb 4-4: new high speed USB device using ehci_hcd and address 47
Nov 28 11:37:16 comp-desktop kernel: [ 7439.354806] usb 4-4: new high speed USB device using ehci_hcd and address 48
Nov 28 11:37:17 comp-desktop kernel: [ 7440.338570] usb 4-4: new high speed USB device using ehci_hcd and address 49
Nov 28 11:37:18 comp-desktop kernel: [ 7441.322387] usb 4-4: new high speed USB device using ehci_hcd and address 50
Nov 28 11:37:18 comp-desktop kernel: [ 7441.842285] usb 4-4: new high speed USB device using ehci_hcd and address 51

$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

On the same computer (dual boot), under XP everything working fine and smooth, I mean cables and flash itself are OK and working properly.

Please help me in this situation, what could cause problems? how can I solve them?
Any help would be welcome.

---

### Post by q11q11 on 2007-12-07
nobody knows?

---

### Post by morgan_greywolf on 2007-12-09
I'm having the same problem, but only with my front USB ports instead of my back.  But I get the same error message you're getting.

If I find the solution, I'll post here.

---

