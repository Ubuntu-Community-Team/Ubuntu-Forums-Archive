---
title: "intel proset wireless (ipw3945) resets when i go into tty1"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by dr_d on 2007-02-12
Hi. I'm using the Intel Pro/Set wireless driver that comes by default in Edgy Eft. I also have NetworkManagerGnome and have commented out everything in /etc/network/interfaces except for the stuff about the loopback interface.

Anyways, when ever I go into console mode (alt+f1) my wireless connection drops out and has to reconnect. I get these weird error messages:

> Feb 13 01:37:44 newport kernel: [17180797.340000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Feb 13 01:37:44 newport kernel: [17180797.340000] ipw3945: Microcode SW error detected.  Restarting.
Feb 13 01:37:45 newport kernel: [17180797.840000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Feb 13 01:37:46 newport kernel: [17180798.832000] ipw3945: Can't stop Rx DMA.
Feb 13 01:37:47 newport kernel: [17180800.436000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Feb 13 01:37:48 newport kernel: [17180801.476000] ipw3945: 3945ABG card ucode DOWNLOAD FAILED 
Feb 13 01:37:48 newport kernel: [17180801.476000] ipw3945: Unable to load firmware: -110
Feb 13 01:37:49 newport kernel: [17180802.472000] ipw3945: 3945ABG card ucode DOWNLOAD FAILED 
Feb 13 01:37:49 newport kernel: [17180802.472000] ipw3945: Unable to load firmware: -110
Feb 13 01:37:50 newport kernel: [17180803.468000] ipw3945: 3945ABG card ucode DOWNLOAD FAILED 
Feb 13 01:37:50 newport kernel: [17180803.468000] ipw3945: Unable to load firmware: -110
Feb 13 01:37:51 newport kernel: [17180804.464000] ipw3945: 3945ABG card ucode DOWNLOAD FAILED 
Feb 13 01:37:51 newport kernel: [17180804.464000] ipw3945: Unable to load firmware: -110
Feb 13 01:37:52 newport kernel: [17180805.460000] ipw3945: 3945ABG card ucode DOWNLOAD FAILED 
Feb 13 01:37:52 newport kernel: [17180805.460000] ipw3945: Unable to load firmware: -110
Feb 13 01:37:53 newport kernel: [17180806.564000] ipw3945: Unable to initialize device after 5 attempts.
Feb 13 01:37:53 newport kernel: [17180806.824000] ipw3945: Detected geography ABG (13 802.11bg channels, 4 802.11a channels)
Feb 13 01:38:21 newport kernel: [17180834.784000] ipw3945: Microcode SW error detected.  Restarting.
Feb 13 01:38:22 newport kernel: [17180835.284000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Feb 13 01:38:22 newport kernel: [17180835.284000] ipw3945: request scan called when driver not ready.
Feb 13 01:38:25 newport kernel: [17180837.272000] ipw3945: Can't stop Rx DMA.
Feb 13 01:38:25 newport kernel: [17180838.636000] ipw3945: Detected geography ABG (13 802.11bg channels, 4 802.11a channels)


Please, someone help me out here!

Thanks,
Dr D

---

