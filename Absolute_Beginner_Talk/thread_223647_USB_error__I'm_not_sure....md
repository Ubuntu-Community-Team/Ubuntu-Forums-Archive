---
title: "USB error?  I'm not sure..."
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by SomeoneStupid on 2006-07-26
Hi, all...

I ran into this problem while trying to mount my ipod.. didn't work, tried rebooting the ipod and laptop, still nothing on fdisk -l..  I read a few HOWTOs on dealing with ipods, and did a dmesg command...  what came out wasn't what I expected.. tried it with different usb devices, and still got a similar output of:

```

...
......
[17180300.712000]     Additional sense: No additional sense information
[17180300.712000] end_request: I/O error, dev sda, sector 106
[17180300.832000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180300.832000] sda: Current: sense key: Medium Error
[17180300.832000]     Additional sense: No additional sense information
[17180300.832000] end_request: I/O error, dev sda, sector 107
[17180300.968000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180300.968000] sda: Current: sense key: Medium Error
[17180300.968000]     Additional sense: No additional sense information
[17180300.968000] end_request: I/O error, dev sda, sector 108
[17180301.100000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180301.100000] sda: Current: sense key: Medium Error
[17180301.100000]     Additional sense: No additional sense information
[17180301.100000] end_request: I/O error, dev sda, sector 101
[17180301.228000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180301.228000] sda: Current: sense key: Medium Error
[17180301.228000]     Additional sense: No additional sense information
[17180301.228000] end_request: I/O error, dev sda, sector 102
[17180301.348000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180301.348000] sda: Current: sense key: Medium Error
[17180301.348000]     Additional sense: No additional sense information
[17180301.348000] end_request: I/O error, dev sda, sector 103
[17180301.484000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180301.484000] sda: Current: sense key: Medium Error
[17180301.484000]     Additional sense: No additional sense information
[17180301.484000] end_request: I/O error, dev sda, sector 104
[17180301.604000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180301.604000] sda: Current: sense key: Medium Error
[17180301.604000]     Additional sense: No additional sense information
[17180301.604000] end_request: I/O error, dev sda, sector 105
[17180301.728000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180301.728000] sda: Current: sense key: Medium Error
[17180301.728000]     Additional sense: No additional sense information
[17180301.728000] end_request: I/O error, dev sda, sector 106
[17180301.848000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180301.848000] sda: Current: sense key: Medium Error
[17180301.848000]     Additional sense: No additional sense information
[17180301.848000] end_request: I/O error, dev sda, sector 107
[17180301.984000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180301.984000] sda: Current: sense key: Medium Error
[17180301.984000]     Additional sense: No additional sense information
[17180301.984000] end_request: I/O error, dev sda, sector 108
[17180302.116000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180302.116000] sda: Current: sense key: Medium Error
[17180302.116000]     Additional sense: No additional sense information
[17180302.116000] end_request: I/O error, dev sda, sector 101
[17180302.236000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180302.236000] sda: Current: sense key: Medium Error
[17180302.236000]     Additional sense: No additional sense information
[17180302.236000] end_request: I/O error, dev sda, sector 102
[17180302.360000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180302.360000] sda: Current: sense key: Medium Error
[17180302.360000]     Additional sense: No additional sense information
[17180302.360000] end_request: I/O error, dev sda, sector 103
[17180302.484000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180302.484000] sda: Current: sense key: Medium Error
[17180302.484000]     Additional sense: No additional sense information
[17180302.484000] end_request: I/O error, dev sda, sector 104
[17180303.148000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180303.148000] sda: Current: sense key: Medium Error
[17180303.148000]     Additional sense: No additional sense information
[17180303.148000] end_request: I/O error, dev sda, sector 105
[17180303.284000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180303.284000] sda: Current: sense key: Medium Error
[17180303.284000]     Additional sense: No additional sense information
[17180303.284000] end_request: I/O error, dev sda, sector 106
[17180303.412000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180303.412000] sda: Current: sense key: Medium Error
[17180303.412000]     Additional sense: No additional sense information
[17180303.412000] end_request: I/O error, dev sda, sector 107
[17180303.576000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17180303.576000] sda: Current: sense key: Medium Error
[17180303.576000]     Additional sense: No additional sense information
[17180303.576000] end_request: I/O error, dev sda, sector 108
[17180303.872000] usb 1-1: USB disconnect, address 4
[17180303.876000]  1:0:0:0: SCSI error: return code = 0x10000
[17180303.876000] end_request: I/O error, dev sda, sector 101
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180303.876000]  1:0:0:0: rejecting I/O to dead device
[17180349.148000] usb 4-1: new high speed USB device using ehci_hcd and address 52
[17180360.692000] usb 4-1: device not accepting address 52, error -110
[17180360.992000] usb 4-1: new high speed USB device using ehci_hcd and address 54
[17180372.536000] usb 4-1: device not accepting address 54, error -110
[17180372.648000] usb 4-1: new high speed USB device using ehci_hcd and address 55
[17180384.192000] usb 4-1: device not accepting address 55, error -110
[17180384.304000] usb 4-1: new high speed USB device using ehci_hcd and address 56
[17180394.728000] usb 4-1: device not accepting address 56, error -110
[17180394.840000] usb 4-1: new high speed USB device using ehci_hcd and address 57
[17180405.264000] usb 4-1: device not accepting address 57, error -110
[17180405.596000] usb 4-1: new high speed USB device using ehci_hcd and address 58
[17180417.140000] usb 4-1: device not accepting address 58, error -110
[17180417.252000] usb 4-1: new high speed USB device using ehci_hcd and address 59
[17180428.796000] usb 4-1: device not accepting address 59, error -110
[17180429.284000] usb 4-1: new high speed USB device using ehci_hcd and address 61
[17180440.828000] usb 4-1: device not accepting address 61, error -110
[17180441.128000] usb 4-1: new high speed USB device using ehci_hcd and address 63
[17180452.672000] usb 4-1: device not accepting address 63, error -110
[17180452.784000] usb 4-1: new high speed USB device using ehci_hcd and address 64
[17180464.328000] usb 4-1: device not accepting address 64, error -110
[17180464.440000] usb 4-1: new high speed USB device using ehci_hcd and address 65
[17180474.864000] usb 4-1: device not accepting address 65, error -110
[17180474.976000] usb 4-1: new high speed USB device using ehci_hcd and address 66
[17180485.400000] usb 4-1: device not accepting address 66, error -110
[17180485.732000] usb 4-1: new high speed USB device using ehci_hcd and address 67
[17180497.276000] usb 4-1: device not accepting address 67, error -110
[17180497.388000] usb 4-1: new high speed USB device using ehci_hcd and address 68
[17180508.932000] usb 4-1: device not accepting address 68, error -110
[17180509.044000] usb 4-1: new high speed USB device using ehci_hcd and address 69
[17180519.468000] usb 4-1: device not accepting address 69, error -110
[17180519.580000] usb 4-1: new high speed USB device using ehci_hcd and address 70
[17180530.004000] usb 4-1: device not accepting address 70, error -110
[17180530.336000] usb 4-1: new high speed USB device using ehci_hcd and address 71
[17180541.880000] usb 4-1: device not accepting address 71, error -110
[17180541.992000] usb 4-1: new high speed USB device using ehci_hcd and address 72
[17180553.536000] usb 4-1: device not accepting address 72, error -110
[17180553.648000] usb 4-1: new high speed USB device using ehci_hcd and address 73
[17180564.072000] usb 4-1: device not accepting address 73, error -110
[17180564.184000] usb 4-1: new high speed USB device using ehci_hcd and address 74
[17180574.608000] usb 4-1: device not accepting address 74, error -110
[17180574.940000] usb 4-1: new high speed USB device using ehci_hcd and address 75

```

any idea what this means?

'appreciated :)

---

### Post by SomeoneStupid on 2006-07-27
anyone? :(

---

### Post by philippe_carlo on 2006-07-27
Have you tried the USB key on another PC? Have you tried different ports? Do you have windows installed, and does it work there?

---

### Post by SomeoneStupid on 2006-07-27
Yeah, I've tried it on different ports, no dice..
Tried on a different pc, worked fine..
Tried it on windows with the same laptop that's having problems and it's worked perfectly..:???:

---

### Post by philippe_carlo on 2006-07-27
Sounds like a bug to me. Are you running Dapper? Maybe updating the kernel, or compiling your own helps.

---

### Post by SomeoneStupid on 2006-08-02
Ah, oh well, thank you very much for you help anyways..

---

