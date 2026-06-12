---
title: "reloading the USB kernel modules"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by feedmecereal on 2007-07-06
In a VMware board, I was told to reload the USB kernel modules (rmmod and then modprobe) so I could get my external USB storage devices working again. How do I do that? And would if affect my USB keyboard and mouse?

---

### Post by shrift on 2007-07-06
You can find out what usb modules are loaded by running this command: ```
lsmod | grep usb
```

that should yield something like this: ```
bmartens@ender:~$ lsmod | grep usb
usb_storage            72896  2 
ide_core              116676  1 usb_storage
usbhid                 29536  0 
hid                    28928  1 usbhid
libusual               18192  1 usb_storage
usblp                  15104  0 
scsi_mod              147084  5 usb_storage,sg,sd_mod,sr_mod,libata
usbcore               137480  7 usb_storage,usbhid,libusual,usblp,ehci_hcd,uhci_hcd

```

I think you probably need to reload the "usbhid" module and "usbcore".

To do that try this:```
sudo modprobe -r usbhid  && sudo modprobe usbhid
``` and then you can try doing that for usbcore as well, but I'm not sure if it will work, as it may be in use. usbhid might be too.

Give that a try though.

---

