---
title: "Macbook Pro 4,1  Keyboard and mouse is sues with 10.04"
date: 2010-07-21
forum: Apple Hardware Users
---

### Post by elendryst on 2010-07-21
The issue appears almost entirely like the keyboard issue in the 10.6.2 release that caused people's mice and keyboards to lock up. Sometimes a few of the keys will work whereas the other keys won't. The issue lasts several seconds and occurs in text fields. Sometimes it happens so strongly Ubuntu restarts back at the login screen.

This shows up in the log viewer:

Jul 21 14:03:36 benjamin-laptop kernel: [ 4861.040523] usb 7-2: USB disconnect, address 54
Jul 21 14:03:37 benjamin-laptop kernel: [ 4861.470213] usb 7-2: new full speed USB device using uhci_hcd and address 55
Jul 21 14:03:37 benjamin-laptop kernel: [ 4861.666442] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:03:37 benjamin-laptop kernel: [ 4861.678808] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input117
Jul 21 14:03:37 benjamin-laptop kernel: [ 4861.680213] apple 0003:05AC:0230.006F: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:03:37 benjamin-laptop kernel: [ 4862.181730] apple 0003:05AC:0230.0070: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:03:37 benjamin-laptop kernel: [ 4862.183655] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input118
Jul 21 14:03:50 benjamin-laptop kernel: [ 4875.040313] usb 7-2: USB disconnect, address 55
Jul 21 14:03:51 benjamin-laptop kernel: [ 4875.480428] usb 7-2: new full speed USB device using uhci_hcd and address 56
Jul 21 14:03:51 benjamin-laptop kernel: [ 4875.675563] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:03:51 benjamin-laptop kernel: [ 4875.688705] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input119
Jul 21 14:03:51 benjamin-laptop kernel: [ 4875.688922] apple 0003:05AC:0230.0071: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:03:51 benjamin-laptop kernel: [ 4876.191735] apple 0003:05AC:0230.0072: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:03:51 benjamin-laptop kernel: [ 4876.193660] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input120
Jul 21 14:04:43 benjamin-laptop kernel: [ 4928.290147] usb 7-2: USB disconnect, address 56
Jul 21 14:04:44 benjamin-laptop kernel: [ 4928.710212] usb 7-2: new full speed USB device using uhci_hcd and address 57
Jul 21 14:04:44 benjamin-laptop kernel: [ 4928.906170] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:04:44 benjamin-laptop kernel: [ 4928.919547] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input121
Jul 21 14:04:44 benjamin-laptop kernel: [ 4928.921798] apple 0003:05AC:0230.0073: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:04:44 benjamin-laptop kernel: [ 4928.984932] usb 7-2: ctrl urb status -75 received
Jul 21 14:04:44 benjamin-laptop kernel: [ 4928.985155] apple 0003:05AC:0230.0074: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:04:44 benjamin-laptop kernel: [ 4928.988062] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input122
Jul 21 14:04:44 benjamin-laptop kernel: [ 4929.040168] usb 7-2: USB disconnect, address 57
Jul 21 14:04:45 benjamin-laptop kernel: [ 4929.420126] usb 7-2: new full speed USB device using uhci_hcd and address 58
Jul 21 14:04:45 benjamin-laptop kernel: [ 4929.615430] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:04:45 benjamin-laptop kernel: [ 4929.627961] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input123
Jul 21 14:04:45 benjamin-laptop kernel: [ 4929.628192] apple 0003:05AC:0230.0075: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:04:45 benjamin-laptop kernel: [ 4930.130600] apple 0003:05AC:0230.0076: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:04:45 benjamin-laptop kernel: [ 4930.132621] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input124
Jul 21 14:04:47 benjamin-laptop kernel: [ 4931.790250] usb 7-2: USB disconnect, address 58
Jul 21 14:04:47 benjamin-laptop kernel: [ 4932.230175] usb 7-2: new full speed USB device using uhci_hcd and address 59
Jul 21 14:04:48 benjamin-laptop kernel: [ 4932.424930] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:04:48 benjamin-laptop kernel: [ 4932.436266] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input125
Jul 21 14:04:48 benjamin-laptop kernel: [ 4932.436477] apple 0003:05AC:0230.0077: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:04:48 benjamin-laptop kernel: [ 4932.941114] apple 0003:05AC:0230.0078: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:04:48 benjamin-laptop kernel: [ 4932.943113] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input126
Jul 21 14:05:15 benjamin-laptop kernel: [ 4959.540324] usb 7-2: USB disconnect, address 59
Jul 21 14:05:15 benjamin-laptop kernel: [ 4959.970220] usb 7-2: new full speed USB device using uhci_hcd and address 60
Jul 21 14:05:15 benjamin-laptop kernel: [ 4960.165650] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:15 benjamin-laptop kernel: [ 4960.178296] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input127
Jul 21 14:05:15 benjamin-laptop kernel: [ 4960.180573] apple 0003:05AC:0230.0079: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:15 benjamin-laptop kernel: [ 4960.244560] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:15 benjamin-laptop kernel: [ 4960.244782] apple 0003:05AC:0230.007A: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:15 benjamin-laptop kernel: [ 4960.246873] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input128
Jul 21 14:05:15 benjamin-laptop kernel: [ 4960.290240] usb 7-2: USB disconnect, address 60
Jul 21 14:05:16 benjamin-laptop kernel: [ 4960.680153] usb 7-2: new full speed USB device using uhci_hcd and address 61
Jul 21 14:05:16 benjamin-laptop kernel: [ 4960.878942] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:16 benjamin-laptop kernel: [ 4960.889330] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input129
Jul 21 14:05:16 benjamin-laptop kernel: [ 4960.889429] apple 0003:05AC:0230.007B: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:16 benjamin-laptop kernel: [ 4960.925898] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:16 benjamin-laptop kernel: [ 4960.926119] apple 0003:05AC:0230.007C: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:16 benjamin-laptop kernel: [ 4960.928038] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input130
Jul 21 14:05:16 benjamin-laptop kernel: [ 4961.050283] usb 7-2: USB disconnect, address 61
Jul 21 14:05:17 benjamin-laptop kernel: [ 4961.442631] usb 7-2: new full speed USB device using uhci_hcd and address 62
Jul 21 14:05:17 benjamin-laptop kernel: [ 4961.637511] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:17 benjamin-laptop kernel: [ 4961.649911] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input131
Jul 21 14:05:17 benjamin-laptop kernel: [ 4961.650354] apple 0003:05AC:0230.007D: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:17 benjamin-laptop kernel: [ 4961.676178] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:17 benjamin-laptop kernel: [ 4961.676292] apple 0003:05AC:0230.007E: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:17 benjamin-laptop kernel: [ 4961.678290] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input132
Jul 21 14:05:17 benjamin-laptop kernel: [ 4961.790245] usb 7-2: USB disconnect, address 62
Jul 21 14:05:17 benjamin-laptop kernel: [ 4962.180219] usb 7-2: new full speed USB device using uhci_hcd and address 63
Jul 21 14:05:18 benjamin-laptop kernel: [ 4962.374900] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:18 benjamin-laptop kernel: [ 4962.388081] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input133
Jul 21 14:05:18 benjamin-laptop kernel: [ 4962.388440] apple 0003:05AC:0230.007F: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:18 benjamin-laptop kernel: [ 4962.891082] apple 0003:05AC:0230.0080: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:18 benjamin-laptop kernel: [ 4962.893068] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input134
Jul 21 14:05:22 benjamin-laptop kernel: [ 4966.540359] usb 7-2: USB disconnect, address 63
Jul 21 14:05:22 benjamin-laptop kernel: [ 4967.070179] usb 7-2: new full speed USB device using uhci_hcd and address 64
Jul 21 14:05:22 benjamin-laptop kernel: [ 4967.266240] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:22 benjamin-laptop kernel: [ 4967.281525] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input135
Jul 21 14:05:22 benjamin-laptop kernel: [ 4967.281736] apple 0003:05AC:0230.0081: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:23 benjamin-laptop kernel: [ 4967.641168] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:23 benjamin-laptop kernel: [ 4967.641700] apple 0003:05AC:0230.0082: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:23 benjamin-laptop kernel: [ 4967.643406] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input136
Jul 21 14:05:23 benjamin-laptop kernel: [ 4967.790193] usb 7-2: USB disconnect, address 64
Jul 21 14:05:23 benjamin-laptop kernel: [ 4968.200213] usb 7-2: new full speed USB device using uhci_hcd and address 65
Jul 21 14:05:24 benjamin-laptop kernel: [ 4968.396766] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:24 benjamin-laptop kernel: [ 4968.408743] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input137
Jul 21 14:05:24 benjamin-laptop kernel: [ 4968.408953] apple 0003:05AC:0230.0083: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:24 benjamin-laptop kernel: [ 4968.913086] apple 0003:05AC:0230.0084: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:24 benjamin-laptop kernel: [ 4968.915027] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input138
Jul 21 14:05:26 benjamin-laptop kernel: [ 4970.790266] usb 7-2: USB disconnect, address 65
Jul 21 14:05:26 benjamin-laptop kernel: [ 4971.230337] usb 7-2: new full speed USB device using uhci_hcd and address 66
Jul 21 14:05:27 benjamin-laptop kernel: [ 4971.427326] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:27 benjamin-laptop kernel: [ 4971.440297] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input139
Jul 21 14:05:27 benjamin-laptop kernel: [ 4971.440507] apple 0003:05AC:0230.0085: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:27 benjamin-laptop kernel: [ 4971.822253] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:27 benjamin-laptop kernel: [ 4971.822448] apple 0003:05AC:0230.0086: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:27 benjamin-laptop kernel: [ 4971.824456] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input140
Jul 21 14:05:27 benjamin-laptop kernel: [ 4972.040299] usb 7-2: USB disconnect, address 66
Jul 21 14:05:28 benjamin-laptop kernel: [ 4972.430205] usb 7-2: new full speed USB device using uhci_hcd and address 67
Jul 21 14:05:28 benjamin-laptop kernel: [ 4972.626026] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:28 benjamin-laptop kernel: [ 4972.640320] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input141
Jul 21 14:05:28 benjamin-laptop kernel: [ 4972.640533] apple 0003:05AC:0230.0087: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:28 benjamin-laptop kernel: [ 4972.700690] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:28 benjamin-laptop kernel: [ 4972.700897] apple 0003:05AC:0230.0088: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:28 benjamin-laptop kernel: [ 4972.703907] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input142
Jul 21 14:05:28 benjamin-laptop kernel: [ 4972.790280] usb 7-2: USB disconnect, address 67
Jul 21 14:05:28 benjamin-laptop kernel: [ 4973.180099] usb 7-2: new full speed USB device using uhci_hcd and address 68
Jul 21 14:05:29 benjamin-laptop kernel: [ 4973.377333] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:29 benjamin-laptop kernel: [ 4973.388599] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input143
Jul 21 14:05:29 benjamin-laptop kernel: [ 4973.389563] apple 0003:05AC:0230.0089: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:29 benjamin-laptop kernel: [ 4973.543205] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:29 benjamin-laptop kernel: [ 4973.543434] apple 0003:05AC:0230.008A: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:29 benjamin-laptop kernel: [ 4973.546335] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input144
Jul 21 14:05:29 benjamin-laptop kernel: [ 4973.793875] usb 7-2: USB disconnect, address 68
Jul 21 14:05:29 benjamin-laptop kernel: [ 4974.280201] usb 7-2: new full speed USB device using uhci_hcd and address 69
Jul 21 14:05:30 benjamin-laptop kernel: [ 4974.475834] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:30 benjamin-laptop kernel: [ 4974.490329] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input145
Jul 21 14:05:30 benjamin-laptop kernel: [ 4974.490556] apple 0003:05AC:0230.008B: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:30 benjamin-laptop kernel: [ 4974.991987] apple 0003:05AC:0230.008C: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:30 benjamin-laptop kernel: [ 4974.994174] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input146
Jul 21 14:05:48 benjamin-laptop kernel: [ 4993.040313] usb 7-2: USB disconnect, address 69
Jul 21 14:05:49 benjamin-laptop kernel: [ 4993.470100] usb 7-2: new full speed USB device using uhci_hcd and address 70
Jul 21 14:05:49 benjamin-laptop kernel: [ 4993.665427] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:49 benjamin-laptop kernel: [ 4993.679942] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input147
Jul 21 14:05:49 benjamin-laptop kernel: [ 4993.680931] apple 0003:05AC:0230.008D: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:49 benjamin-laptop kernel: [ 4993.703215] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:49 benjamin-laptop kernel: [ 4993.703404] apple 0003:05AC:0230.008E: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:49 benjamin-laptop kernel: [ 4993.705382] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input148
Jul 21 14:05:49 benjamin-laptop kernel: [ 4993.790276] usb 7-2: USB disconnect, address 70
Jul 21 14:05:49 benjamin-laptop kernel: [ 4994.190216] usb 7-2: new full speed USB device using uhci_hcd and address 71
Jul 21 14:05:50 benjamin-laptop kernel: [ 4994.384897] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:50 benjamin-laptop kernel: [ 4994.395692] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input149
Jul 21 14:05:50 benjamin-laptop kernel: [ 4994.395900] apple 0003:05AC:0230.008F: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:50 benjamin-laptop kernel: [ 4994.598644] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:50 benjamin-laptop kernel: [ 4994.598856] apple 0003:05AC:0230.0090: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:50 benjamin-laptop kernel: [ 4994.601134] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input150
Jul 21 14:05:50 benjamin-laptop kernel: [ 4994.790376] usb 7-2: USB disconnect, address 71
Jul 21 14:05:50 benjamin-laptop kernel: [ 4995.210169] usb 7-2: new full speed USB device using uhci_hcd and address 72
Jul 21 14:05:51 benjamin-laptop kernel: [ 4995.407412] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:51 benjamin-laptop kernel: [ 4995.421680] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input151
Jul 21 14:05:51 benjamin-laptop kernel: [ 4995.421890] apple 0003:05AC:0230.0091: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:51 benjamin-laptop kernel: [ 4995.665198] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:51 benjamin-laptop kernel: [ 4995.665400] apple 0003:05AC:0230.0092: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:51 benjamin-laptop kernel: [ 4995.667360] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input152
Jul 21 14:05:51 benjamin-laptop kernel: [ 4995.792792] usb 7-2: USB disconnect, address 72
Jul 21 14:05:51 benjamin-laptop kernel: [ 4996.190212] usb 7-2: new full speed USB device using uhci_hcd and address 73
Jul 21 14:05:52 benjamin-laptop kernel: [ 4996.384896] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:52 benjamin-laptop kernel: [ 4996.397357] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input153
Jul 21 14:05:52 benjamin-laptop kernel: [ 4996.397932] apple 0003:05AC:0230.0093: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:52 benjamin-laptop kernel: [ 4996.423641] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:52 benjamin-laptop kernel: [ 4996.423867] apple 0003:05AC:0230.0094: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:52 benjamin-laptop kernel: [ 4996.425802] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input154
Jul 21 14:05:52 benjamin-laptop kernel: [ 4996.542784] usb 7-2: USB disconnect, address 73
Jul 21 14:05:52 benjamin-laptop kernel: [ 4996.940213] usb 7-2: new full speed USB device using uhci_hcd and address 74
Jul 21 14:05:52 benjamin-laptop kernel: [ 4997.135273] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:52 benjamin-laptop kernel: [ 4997.147876] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input155
Jul 21 14:05:52 benjamin-laptop kernel: [ 4997.148217] apple 0003:05AC:0230.0095: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:52 benjamin-laptop kernel: [ 4997.205964] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:52 benjamin-laptop kernel: [ 4997.206147] apple 0003:05AC:0230.0096: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:52 benjamin-laptop kernel: [ 4997.208169] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input156
Jul 21 14:05:52 benjamin-laptop kernel: [ 4997.290280] usb 7-2: USB disconnect, address 74
Jul 21 14:05:53 benjamin-laptop kernel: [ 4997.700211] usb 7-2: new full speed USB device using uhci_hcd and address 75
Jul 21 14:05:53 benjamin-laptop kernel: [ 4997.894655] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:53 benjamin-laptop kernel: [ 4997.907984] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input157
Jul 21 14:05:53 benjamin-laptop kernel: [ 4997.908349] apple 0003:05AC:0230.0097: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:54 benjamin-laptop kernel: [ 4998.409838] apple 0003:05AC:0230.0098: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:54 benjamin-laptop kernel: [ 4998.411752] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input158
Jul 21 14:05:58 benjamin-laptop kernel: [ 5002.790289] usb 7-2: USB disconnect, address 75
Jul 21 14:05:58 benjamin-laptop kernel: [ 5003.220083] usb 7-2: new full speed USB device using uhci_hcd and address 76
Jul 21 14:05:59 benjamin-laptop kernel: [ 5003.417418] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:05:59 benjamin-laptop kernel: [ 5003.431626] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input159
Jul 21 14:05:59 benjamin-laptop kernel: [ 5003.431838] apple 0003:05AC:0230.0099: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:05:59 benjamin-laptop kernel: [ 5003.667205] usb 7-2: ctrl urb status -75 received
Jul 21 14:05:59 benjamin-laptop kernel: [ 5003.667429] apple 0003:05AC:0230.009A: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:05:59 benjamin-laptop kernel: [ 5003.669363] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input160
Jul 21 14:05:59 benjamin-laptop kernel: [ 5003.790268] usb 7-2: USB disconnect, address 76
Jul 21 14:05:59 benjamin-laptop kernel: [ 5004.200129] usb 7-2: new full speed USB device using uhci_hcd and address 77
Jul 21 14:06:00 benjamin-laptop kernel: [ 5004.397918] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:06:00 benjamin-laptop kernel: [ 5004.409100] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input161
Jul 21 14:06:00 benjamin-laptop kernel: [ 5004.409447] apple 0003:05AC:0230.009B: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:06:00 benjamin-laptop kernel: [ 5004.914085] apple 0003:05AC:0230.009C: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:06:00 benjamin-laptop kernel: [ 5004.916013] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input162
Jul 21 14:07:01 benjamin-laptop kernel: [ 5065.540282] usb 7-2: USB disconnect, address 77
Jul 21 14:07:01 benjamin-laptop kernel: [ 5066.030068] usb 7-2: new full speed USB device using uhci_hcd and address 78
Jul 21 14:07:01 benjamin-laptop kernel: [ 5066.225804] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:07:01 benjamin-laptop kernel: [ 5066.240096] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input163
Jul 21 14:07:01 benjamin-laptop kernel: [ 5066.240316] apple 0003:05AC:0230.009D: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:07:02 benjamin-laptop kernel: [ 5066.741012] apple 0003:05AC:0230.009E: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:07:02 benjamin-laptop kernel: [ 5066.742961] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input164
Jul 21 14:08:42 benjamin-laptop kernel: [ 5167.294361] usb 7-2: USB disconnect, address 78
Jul 21 14:08:43 benjamin-laptop kernel: [ 5167.710406] usb 7-2: new full speed USB device using uhci_hcd and address 79
Jul 21 14:08:43 benjamin-laptop kernel: [ 5167.905561] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:08:43 benjamin-laptop kernel: [ 5167.916791] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input165
Jul 21 14:08:43 benjamin-laptop kernel: [ 5167.917177] apple 0003:05AC:0230.009F: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:08:43 benjamin-laptop kernel: [ 5168.139218] usb 7-2: ctrl urb status -75 received
Jul 21 14:08:43 benjamin-laptop kernel: [ 5168.139361] apple 0003:05AC:0230.00A0: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:08:43 benjamin-laptop kernel: [ 5168.141321] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input166
Jul 21 14:08:43 benjamin-laptop kernel: [ 5168.290293] usb 7-2: USB disconnect, address 79
Jul 21 14:08:44 benjamin-laptop kernel: [ 5168.680204] usb 7-2: new full speed USB device using uhci_hcd and address 80
Jul 21 14:08:44 benjamin-laptop kernel: [ 5168.877585] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:08:44 benjamin-laptop kernel: [ 5168.888789] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input167
Jul 21 14:08:44 benjamin-laptop kernel: [ 5168.890785] apple 0003:05AC:0230.00A1: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:08:45 benjamin-laptop kernel: [ 5169.393510] apple 0003:05AC:0230.00A2: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:08:45 benjamin-laptop kernel: [ 5169.395395] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input168
Jul 21 14:10:21 benjamin-laptop kernel: [ 5265.540266] usb 7-2: USB disconnect, address 80
Jul 21 14:10:21 benjamin-laptop kernel: [ 5266.020198] usb 7-2: new full speed USB device using uhci_hcd and address 81
Jul 21 14:10:21 benjamin-laptop kernel: [ 5266.214584] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:10:21 benjamin-laptop kernel: [ 5266.227770] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input169
Jul 21 14:10:21 benjamin-laptop kernel: [ 5266.227984] apple 0003:05AC:0230.00A3: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:10:22 benjamin-laptop kernel: [ 5266.388259] usb 7-2: ctrl urb status -75 received
Jul 21 14:10:22 benjamin-laptop kernel: [ 5266.388508] apple 0003:05AC:0230.00A4: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:10:22 benjamin-laptop kernel: [ 5266.390576] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input170
Jul 21 14:10:22 benjamin-laptop kernel: [ 5266.390847] usb 7-2: USB disconnect, address 81
Jul 21 14:10:22 benjamin-laptop kernel: [ 5266.800099] usb 7-2: new full speed USB device using uhci_hcd and address 82
Jul 21 14:10:22 benjamin-laptop kernel: [ 5266.995511] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:10:22 benjamin-laptop kernel: [ 5267.008817] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input171
Jul 21 14:10:22 benjamin-laptop kernel: [ 5267.009034] apple 0003:05AC:0230.00A5: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:10:22 benjamin-laptop kernel: [ 5267.042217] usb 7-2: ctrl urb status -75 received
Jul 21 14:10:22 benjamin-laptop kernel: [ 5267.042437] apple 0003:05AC:0230.00A6: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:10:22 benjamin-laptop kernel: [ 5267.045457] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input172
Jul 21 14:10:22 benjamin-laptop kernel: [ 5267.290299] usb 7-2: USB disconnect, address 82
Jul 21 14:10:23 benjamin-laptop kernel: [ 5267.680204] usb 7-2: new full speed USB device using uhci_hcd and address 83
Jul 21 14:10:23 benjamin-laptop kernel: [ 5267.877488] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:10:23 benjamin-laptop kernel: [ 5267.891752] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input173
Jul 21 14:10:23 benjamin-laptop kernel: [ 5267.891959] apple 0003:05AC:0230.00A7: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:10:23 benjamin-laptop kernel: [ 5267.943319] usb 7-2: ctrl urb status -75 received
Jul 21 14:10:23 benjamin-laptop kernel: [ 5267.943546] apple 0003:05AC:0230.00A8: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:10:23 benjamin-laptop kernel: [ 5267.945522] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input174
Jul 21 14:10:23 benjamin-laptop kernel: [ 5268.040355] usb 7-2: USB disconnect, address 83
Jul 21 14:10:24 benjamin-laptop kernel: [ 5268.450179] usb 7-2: new full speed USB device using uhci_hcd and address 84
Jul 21 14:10:24 benjamin-laptop kernel: [ 5268.645592] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:10:24 benjamin-laptop kernel: [ 5268.658736] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input175
Jul 21 14:10:24 benjamin-laptop kernel: [ 5268.658940] apple 0003:05AC:0230.00A9: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:10:24 benjamin-laptop kernel: [ 5269.161517] apple 0003:05AC:0230.00AA: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:10:24 benjamin-laptop kernel: [ 5269.163435] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input176
Jul 21 14:10:28 benjamin-laptop kernel: [ 5272.540285] usb 7-2: USB disconnect, address 84
Jul 21 14:10:28 benjamin-laptop kernel: [ 5272.980210] usb 7-2: new full speed USB device using uhci_hcd and address 85
Jul 21 14:10:28 benjamin-laptop kernel: [ 5273.175627] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:10:28 benjamin-laptop kernel: [ 5273.185808] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input177
Jul 21 14:10:28 benjamin-laptop kernel: [ 5273.186157] apple 0003:05AC:0230.00AB: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:10:29 benjamin-laptop kernel: [ 5273.691518] apple 0003:05AC:0230.00AC: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:10:29 benjamin-laptop kernel: [ 5273.693511] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input178
Jul 21 14:11:00 benjamin-laptop kernel: [ 5304.540281] usb 7-2: USB disconnect, address 85
Jul 21 14:11:00 benjamin-laptop kernel: [ 5304.970208] usb 7-2: new full speed USB device using uhci_hcd and address 86
Jul 21 14:11:00 benjamin-laptop kernel: [ 5305.165618] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:11:00 benjamin-laptop kernel: [ 5305.178318] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input179
Jul 21 14:11:00 benjamin-laptop kernel: [ 5305.179603] apple 0003:05AC:0230.00AD: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:11:00 benjamin-laptop kernel: [ 5305.235234] usb 7-2: ctrl urb status -75 received
Jul 21 14:11:00 benjamin-laptop kernel: [ 5305.235478] apple 0003:05AC:0230.00AE: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:11:00 benjamin-laptop kernel: [ 5305.237684] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input180
Jul 21 14:11:00 benjamin-laptop kernel: [ 5305.290193] usb 7-2: USB disconnect, address 86
Jul 21 14:11:01 benjamin-laptop kernel: [ 5305.690110] usb 7-2: new full speed USB device using uhci_hcd and address 87
Jul 21 14:11:01 benjamin-laptop kernel: [ 5305.945599] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:11:01 benjamin-laptop kernel: [ 5305.955817] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input181
Jul 21 14:11:01 benjamin-laptop kernel: [ 5305.956033] apple 0003:05AC:0230.00AF: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:11:02 benjamin-laptop kernel: [ 5306.347325] usb 7-2: ctrl urb status -75 received
Jul 21 14:11:02 benjamin-laptop kernel: [ 5306.347550] apple 0003:05AC:0230.00B0: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:11:02 benjamin-laptop kernel: [ 5306.349444] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input182
Jul 21 14:11:02 benjamin-laptop kernel: [ 5306.540298] usb 7-2: USB disconnect, address 87
Jul 21 14:11:02 benjamin-laptop kernel: [ 5306.990216] usb 7-2: new full speed USB device using uhci_hcd and address 88
Jul 21 14:11:02 benjamin-laptop kernel: [ 5307.186597] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:11:02 benjamin-laptop kernel: [ 5307.198214] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input183
Jul 21 14:11:02 benjamin-laptop kernel: [ 5307.198435] apple 0003:05AC:0230.00B1: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:11:03 benjamin-laptop kernel: [ 5307.701420] apple 0003:05AC:0230.00B2: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:11:03 benjamin-laptop kernel: [ 5307.703417] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input184
Jul 21 14:11:03 benjamin-laptop kernel: [ 5308.040297] usb 7-2: USB disconnect, address 88
Jul 21 14:11:04 benjamin-laptop kernel: [ 5308.500285] usb 7-2: new full speed USB device using uhci_hcd and address 89
Jul 21 14:11:04 benjamin-laptop kernel: [ 5308.701984] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:11:04 benjamin-laptop kernel: [ 5308.712844] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input185
Jul 21 14:11:04 benjamin-laptop kernel: [ 5308.713066] apple 0003:05AC:0230.00B3: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:11:04 benjamin-laptop kernel: [ 5309.191231] usb 7-2: ctrl urb status -75 received
Jul 21 14:11:04 benjamin-laptop kernel: [ 5309.191600] apple 0003:05AC:0230.00B4: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:11:04 benjamin-laptop kernel: [ 5309.193421] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input186
Jul 21 14:11:04 benjamin-laptop kernel: [ 5309.193707] usb 7-2: USB disconnect, address 89
Jul 21 14:11:05 benjamin-laptop kernel: [ 5309.590214] usb 7-2: new full speed USB device using uhci_hcd and address 90
Jul 21 14:11:05 benjamin-laptop kernel: [ 5309.797599] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:11:05 benjamin-laptop kernel: [ 5309.812922] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input187
Jul 21 14:11:05 benjamin-laptop kernel: [ 5309.815243] apple 0003:05AC:0230.00B5: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:11:05 benjamin-laptop kernel: [ 5309.883294] __ratelimit: 9 callbacks suppressed
Jul 21 14:11:05 benjamin-laptop kernel: [ 5309.883303] Xorg[1221] general protection ip:46fca4 sp:7fffe1154fa0 error:0 in Xorg[400000+1be000]
Jul 21 14:11:05 benjamin-laptop kernel: [ 5310.051205] usb 7-2: ctrl urb status -75 received
Jul 21 14:11:05 benjamin-laptop kernel: [ 5310.051893] apple 0003:05AC:0230.00B6: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:11:05 benjamin-laptop kernel: [ 5310.053314] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input188
Jul 21 14:11:05 benjamin-laptop kernel: [ 5310.300252] usb 7-2: USB disconnect, address 90
Jul 21 14:11:07 benjamin-laptop pulseaudio[6207]: pid.c: Stale PID file, overwriting.
Jul 21 14:11:07 benjamin-laptop pulseaudio[6207]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-iiM0DkYv9N: Connection refused
Jul 21 14:11:07 benjamin-laptop kernel: [ 5311.450063] usb 7-2: new full speed USB device using uhci_hcd and address 91
Jul 21 14:11:07 benjamin-laptop kernel: [ 5311.654309] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:11:07 benjamin-laptop kernel: [ 5311.665761] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input189
Jul 21 14:11:07 benjamin-laptop kernel: [ 5311.665849] apple 0003:05AC:0230.00B7: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:11:07 benjamin-laptop kernel: [ 5311.677204] usb 7-2: ctrl urb status -75 received
Jul 21 14:11:07 benjamin-laptop kernel: [ 5311.677298] apple 0003:05AC:0230.00B8: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:11:07 benjamin-laptop kernel: [ 5311.679565] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input190
Jul 21 14:11:07 benjamin-laptop kernel: [ 5311.790230] usb 7-2: USB disconnect, address 91
Jul 21 14:11:08 benjamin-laptop kernel: [ 5312.452541] usb 7-2: new full speed USB device using uhci_hcd and address 92
Jul 21 14:11:08 benjamin-laptop kernel: [ 5312.651333] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:11:08 benjamin-laptop kernel: [ 5312.662784] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input191
Jul 21 14:11:08 benjamin-laptop kernel: [ 5312.662873] apple 0003:05AC:0230.00B9: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:11:08 benjamin-laptop kernel: [ 5313.167320] apple 0003:05AC:0230.00BA: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:11:08 benjamin-laptop kernel: [ 5313.169301] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input192
Jul 21 14:13:20 benjamin-laptop kernel: [ 5444.790493] usb 7-2: USB disconnect, address 92
Jul 21 14:13:20 benjamin-laptop kernel: [ 5445.220215] usb 7-2: new full speed USB device using uhci_hcd and address 93
Jul 21 14:13:21 benjamin-laptop kernel: [ 5445.415185] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:13:21 benjamin-laptop kernel: [ 5445.431366] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input193
Jul 21 14:13:21 benjamin-laptop kernel: [ 5445.431571] apple 0003:05AC:0230.00BB: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:13:21 benjamin-laptop kernel: [ 5445.931123] apple 0003:05AC:0230.00BC: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:13:21 benjamin-laptop kernel: [ 5445.933280] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input194
Jul 21 14:13:22 benjamin-laptop kernel: [ 5447.290310] usb 7-2: USB disconnect, address 93
Jul 21 14:13:23 benjamin-laptop kernel: [ 5447.740220] usb 7-2: new full speed USB device using uhci_hcd and address 94
Jul 21 14:13:23 benjamin-laptop kernel: [ 5447.935185] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:13:23 benjamin-laptop kernel: [ 5447.950388] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input195
Jul 21 14:13:23 benjamin-laptop kernel: [ 5447.950601] apple 0003:05AC:0230.00BD: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:13:24 benjamin-laptop kernel: [ 5448.451036] apple 0003:05AC:0230.00BE: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:13:24 benjamin-laptop kernel: [ 5448.453123] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input196
Jul 21 14:13:38 benjamin-laptop kernel: [ 5463.040326] usb 7-2: USB disconnect, address 94
Jul 21 14:13:39 benjamin-laptop kernel: [ 5463.480234] usb 7-2: new full speed USB device using uhci_hcd and address 95
Jul 21 14:13:39 benjamin-laptop kernel: [ 5463.675180] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:13:39 benjamin-laptop kernel: [ 5463.687297] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input197
Jul 21 14:13:39 benjamin-laptop kernel: [ 5463.687504] apple 0003:05AC:0230.00BF: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:13:39 benjamin-laptop kernel: [ 5463.944910] usb 7-2: ctrl urb status -75 received
Jul 21 14:13:39 benjamin-laptop kernel: [ 5463.945137] apple 0003:05AC:0230.00C0: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:13:39 benjamin-laptop kernel: [ 5463.948034] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input198
Jul 21 14:13:39 benjamin-laptop kernel: [ 5464.040277] usb 7-2: USB disconnect, address 95
Jul 21 14:13:40 benjamin-laptop kernel: [ 5464.430225] usb 7-2: new full speed USB device using uhci_hcd and address 96
Jul 21 14:13:40 benjamin-laptop kernel: [ 5464.627199] usb 7-2: configuration #1 chosen from 1 choice
Jul 21 14:13:40 benjamin-laptop kernel: [ 5464.641498] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input199
Jul 21 14:13:40 benjamin-laptop kernel: [ 5464.641886] apple 0003:05AC:0230.00C1: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Jul 21 14:13:40 benjamin-laptop kernel: [ 5465.143028] apple 0003:05AC:0230.00C2: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Jul 21 14:13:40 benjamin-laptop kernel: [ 5465.145108] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input200

---

### Post by raumkundschafter on 2010-10-12
ej elendryst
same thing on my 4.1 macbook with 10.04 and 2.6.32-25-generic-pae kernel. 
it might be a hardware issue as stated in this thread [http://ubuntuforums.org/showthread.php?t=840040&page=28](http://ubuntuforums.org/showthread.php?t=840040&page=28)
but as i do not have another computer at hand and as there're quite some people dealing with this problem it might be also a driver problem - especially after resume it's very significant. though i don't know where to start hunting this bug and in osx this is not an issue at all...

---

### Post by raumkundschafter on 2010-10-12
a bug report i filed the other day: [https://bugs.launchpad.net/ubuntu/+bug/601132](https://bugs.launchpad.net/ubuntu/+bug/601132)

---

