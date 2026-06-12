---
title: "Need help with webcam"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by nitewing98 on 2006-11-25
Are there any webcam gurus out there?  I need help setting up a webcam.  The cam is an Argus PC300 webcam that has a built-in Mic.  The sound system likes the mic and will use it, but no joy on the video. The light on the cam comes on, and the device is recognized by the usb bus. 

I've done enough "due diligence" (i.e.--research) to realize that the cam has an OmniVision OV518+ chipset and the ov511 driver SEEMS to recognize it, but Camorama won't give me any love.

When I plug in the cam, dmesg gives me: 
[17193907.416000] drivers/usb/media/ov511/ov511.c: USB OV518+ video device found
[17193907.416000] drivers/usb/media/ov511/ov511.c: Device revision 2
[17193907.452000] drivers/usb/media/ov511/ov511.c: Compression required with OV518...enabling
[17193908.036000] drivers/usb/media/ov511/ov511.c: Sensor is an OV7620
[17193909.188000] drivers/usb/media/ov511/ov511.c: Device at usb-0000:00:07.4-3 registered to minor 0
[17193909.188000] usbcore: registered new driver ov511
[17193909.188000] drivers/usb/media/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver

but when I launch Camorama, it throws a dialog box that says:
Could not connect to video device (/dev/video0)
Please check connection.

Any ideas?

---

### Post by crispy_420 on 2006-11-30
Same issue here, anyone?

---

### Post by DSn0wMan on 2006-11-30
I have not tried this, but maybe it will help.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by nitewing98 on 2006-12-03
DSn0wMan,

Thanks for the link, but alas, it didn't help.  The ov511 driver didn't work and the ov51x driver bombed with an error message in french that locked up the installer.

The cam I have has an ov518+, and apparently isn't supported by this software.

Anyone else have any ideas?

---

