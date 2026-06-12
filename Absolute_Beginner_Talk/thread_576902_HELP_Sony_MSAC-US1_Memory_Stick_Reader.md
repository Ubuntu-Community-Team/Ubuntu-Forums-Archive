---
title: "HELP: Sony MSAC-US1 Memory Stick Reader"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by cristian10 on 2007-10-15
Hi,

The system does recognize the USB Sony MSAC-US1 memory stick reader as an external floppy disc, but when I try to open it I get the following message:

"Unable to mount media. There is probably no media in the drive"

Can anybody tell me what to do? 

I am using Ubuntu 7.04 (generic)

Thank you very much.

Regards,

Cristian10

---

### Post by fred168 on 2007-11-05
I get the same "Unable to mount media, there is probably no media in the drive", with a GE USB MemoryStick Card reader (trying to read a SanDisk Memory Stick PRO DUO flash card). Oddly it worked fine the first time but has failed ever since---it does still come up as "Multi Flash Reader" in the "computer" file browser, but gives the above error when this is double clicked.  It also fails when I reboot into Windows XP though, so possibly this a problem with my card reader. Does anyone know how to debug this situation?

Here's some output from tail -f /var/log/messages:

Nov  5 20:10:50 dhcp164 kernel: [  555.100000] usb 7-1: new high speed USB device using ehci_hcd and address 7
Nov  5 20:10:50 dhcp164 kernel: [  555.232000] usb 7-1: configuration #1 chosen from 1 choice
Nov  5 20:10:50 dhcp164 kernel: [  555.232000] scsi6 : SCSI emulation for USB Mass Storage devices
Nov  5 20:10:55 dhcp164 kernel: [  560.236000] scsi 6:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
Nov  5 20:10:55 dhcp164 kernel: [  560.360000] sd 6:0:0:0: Attached scsi removable disk sdb
Nov  5 20:10:55 dhcp164 kernel: [  560.360000] sd 6:0:0:0: Attached scsi generic sg1 type 0

---

