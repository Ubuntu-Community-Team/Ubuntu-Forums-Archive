---
title: "VirtualBox USB Support"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by fraser_m on 2008-01-22
When I try to boot my Windows XP VM in VirtualBox, with a USB flash drive attached, I get this sexy little error:
```

Not permitted to open the USB device, check usbfs options.


Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


```

And the iPod:
```

Failed to create a proxy device for the USB device. (Error: VERR_FILE_NOT_FOUND).


Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

Any help would be nice...

---

### Post by compiledkernel on 2008-01-22
[http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices](http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices)

---

### Post by fraser_m on 2008-01-22
This link is broken...

---

### Post by p_quarles on 2008-01-22
[http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices](http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices)

(the link was broken by an auto-smiley that got added by the forum software).

---

### Post by pyman on 2008-01-22
Thanks for the link that fixed mine :)

---

### Post by echo6 on 2008-01-22
If you are using version 1.5.4 there appears to be a problem with it,  try 1.5.2
[http://www.virtualbox.org/download/1.5.2/](http://www.virtualbox.org/download/1.5.2/)
In 1.5.2 they have added support for usb2 ehci, I think possibly it's broken!

---

