---
title: "Ubuntu and more than 2 USB devices = strange USB problems"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by waffer on 2007-08-08
I'm on Ubuntu 6.06 right now and I was going to burn the latest Ubuntu version to a cd. Because of this I plugged my external cd/dvd burner in and suddenly my USB mouse started lagging. Actually it happens when I have more than 1 USB device plugged in (using an USB mouse right now working fine). For this reason I switched from Windows XP to Ubuntu ! (Because plugging in more than 1 USB device would crash the "older" one and only the newer one (so only my external dvd burner in this case) would work). I thought linux would fix this but no. Luckely it provides more logging but I don't know if its going to help.
These are the things I'm 100% sure about:

-Plugging in more than 1 USB device slows down USB (Linux) or crashes the "older" USB device (Windows XP)
-Disabling the Enhanced USB controller in Windows XP would fix this problem (so any number of USB devices would work without crashing but only at USB 1 speeds :( which I certainly don't want with my external HDD)
-CPU usage stays low like it should be

OK this shows up in my logs after plugging in the second USB device:

Aug  9 02:13:45 waffer-desktop kernel: [17180003.064000] drivers/usb/input/hid-core.c: input irq status -32 received
Aug  9 02:13:45 waffer-desktop kernel: [17180003.512000] drivers/usb/input/hid-core.c: input irq status -32 received
Aug  9 02:13:47 waffer-desktop kernel: [17180004.912000] drivers/usb/input/hid-core.c: input irq status -32 received
Aug  9 02:13:50 waffer-desktop kernel: [17180007.844000]   Vendor: FREECOM_  Model: DVD+/-RW16N8      Rev: FR03
Aug  9 02:13:50 waffer-desktop kernel: [17180007.844000]   Type:   CD-ROM                             ANSI SCSI revision: 00
Aug  9 02:13:50 waffer-desktop kernel: [17180007.900000] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Aug  9 02:13:50 waffer-desktop kernel: [17180007.916000] sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug  9 02:13:50 waffer-desktop kernel: [17180008.396000] drivers/usb/input/hid-core.c: input irq status -71 received
Aug  9 02:13:57 waffer-desktop kernel: [17180015.388000] drivers/usb/input/hid-core.c: input irq status -32 received
Aug  9 02:14:03 waffer-desktop kernel: [17180021.100000] drivers/usb/input/hid-core.c: input irq status -32 received
Aug  9 02:14:03 waffer-desktop kernel: [17180021.540000] drivers/usb/input/hid-core.c: input irq status -32 received

These messages go on forever at what seems to be random times until I remove the second USB device

The 4 usb ports are integrated on my motherboard (asrock k7s8x)

---

### Post by Al3xK3aton on 2007-08-08
Make sure you download the newest drivers; if that doesn't work, just use a PS/2 mouse instead. They are more compatible with older computers anyway, just in case you have to migrate your mouse to an older computer.

---

### Post by waffer on 2007-08-08
OK, I just disabled USB 2 in the BIOS (which is the latest version). It works without slowdowns or error messages now, its just normally slow because of USB 1. I really want 2 or more USB devices to work at USB 2 so no workarounds like a PS/2 mouse...

---

### Post by asmoore82 on 2007-08-08
try making sure your devices are plugged as far apart as possible ... 
like USB ports 1 of 4 and 4 of 4.

---

