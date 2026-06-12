---
title: "1394 detection problem? HELP"
date: 2005-09-29
forum: Apple PPC Users
---

### Post by grimmson on 2005-09-29
Hello all. Noob here troubleshooting a boot problem. Looks like 1394 might have a problem and I don't have any 1394 devices but need usb. keep in mind I have a ppc g3 400 ati 7000 256.
Sep 29 10:00:18 localhost kernel: usb 1-1: new low speed USB device using ohci_h cd and address 5
Sep 29 10:00:18 localhost kernel: usbcore: registered new driver hiddev
Sep 29 10:00:18 localhost kernel: input: USB HID v1.10 Keyboard [Microsoft Inter net Keyboard Pro] on usb-0000:01:06.0-2.1
Sep 29 10:00:18 localhost kernel: input: USB HID v1.10 Device [Microsoft Interne t Keyboard Pro] on usb-0000:01:06.0-2.1
Sep 29 10:00:18 localhost kernel: input: USB HID v1.00 Mouse [ARROW STRONG USB 3 D Mouse] on usb-0000:01:06.0-1
Sep 29 10:00:18 localhost kernel: usbcore: registered new driver usbhid
Sep 29 10:00:18 localhost kernel: drivers/usb/input/hid-core.c: v2.0:USB HID cor e driver
Sep 29 10:00:18 localhost kernel: NET: Registered protocol family 10
Sep 29 10:00:18 localhost kernel: Disabled Privacy Extensions on device c025bf5c (lo)
Sep 29 10:00:18 localhost kernel: IPv6 over IPv4 tunneling driver
Sep 29 10:00:27 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Sep 29 10:00:27 localhost kernel: [drm] Initialized drm 1.0.0 20040925
Sep 29 10:00:27 localhost kernel: [drm] Initialized radeon 1.14.0 20050125 on mi nor 0: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
Sep 29 10:00:28 localhost kernel: drivers/usb/input/hid-input.c: event field not found
Sep 29 10:02:03 localhost syslogd 1.4.1#16ubuntu6: restart.
Sep 29 10:02:04 localhost kernel: Inspecting /boot/System.map-2.6.10-5-powerpc
Sep 29 10:02:04 localhost kernel: Loaded 31227 symbols from /boot/System.map-2.6 .10-5-powerpc.
Sep 29 10:02:04 localhost kernel: Symbols match kernel version 2.6.10.
Sep 29 10:02:04 localhost kernel: No module symbols loaded - kernel modules not enabled.
Sep 29 10:02:04 localhost kernel: ) on request
Sep 29 10:02:04 localhost kernel: pcilynx0: bus reset interrupt
Sep 29 10:02:04 localhost kernel: pcilynx0: SelfID process finished (phyid 0, ro ot)
Sep 29 10:02:04 localhost kernel: ieee1394: SelfIDs failed monotony check with 2 2/0
Sep 29 10:02:04 localhost kernel: ieee1394: Error in SelfID stage, resetting
Sep 29 10:02:04 localhost kernel: pcilynx0: resetting bus (long bus reset) on re quest
Sep 29 10:02:04 localhost kernel: pcilynx0: bus reset interrupt
Sep 29 10:02:04 localhost kernel: pcilynx0: SelfID process finished (phyid 0, ro ot)
Sep 29 10:02:04 localhost kernel: ieee1394: SelfIDs failed monotony check with 2 2/0
Sep 29 10:02:04 localhost kernel: ieee1394: Error in SelfID stage, resetting
Sep 29 10:02:04 localhost kernel: pcilynx0: resetting bus (long bus reset) on re quest
Sep 29 10:02:04 localhost kernel: pcilynx0: bus reset interrupt
Sep 29 10:02:04 localhost kernel: pcilynx0: SelfID process finished (phyid 0, ro ot)
Sep 29 10:02:04 localhost kernel: ieee1394: SelfIDs failed monotony check with 2
Loop problem I think. Thanks for any help.

---

### Post by grimmson on 2005-09-29
I have a ppc (mac) with a ati7000. Install went fine, boots fine to just b 4 the login screen. I get a black screen, circle, arrow (mouse) and It doesn't post loging screen (like it should.) I work around this by hitting ctrl,alt f1. I can then log into terminal or hit f7 and see the graphical login. I assume but hitting ctrl,alt f1 at the right time I interupt the boot process b 4 the error (may require several reboots to time it right.) Any thoughts are appriciated.

---

