---
title: "Macbook 3,1 users - what idProduct is your iSight camera?"
date: 2008-01-31
forum: Apple Intel Users
---

### Post by bluec on 2008-01-31
Hi macbook 3,1 users. Could a few of you post the following info for me please?

1) output of "sudo lsusb"
2) country of origin of your macbook 3,1
3) which model is it - not sure how to refer to these, so lets go "1 = cheapest, 2 = middle, 3 = the most expensive one"

Reason I ask is that lots of you seem to have this in your lsusb...

"ID 05ac:8300 Apple, Inc. Built-in iSight "

with the idProduct being 8300, but here, I have an idProduct of 8501. Seems odd - I thought all macbooks had the same hardware.

my answers:

1)
Bus 002 Device 006: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]
Bus 002 Device 002: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 002 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 05ac:022a Apple, Inc. Internal Keyboard/Trackpad (MacBook Pro) (ISO)
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 05ac:8205 Apple, Inc. Bluetooth HCI MacBookPro
Bus 003 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 001: ID 0000:0000

2) UK

3) 1 - cheapest model

TIA

---

### Post by cyberdork33 on 2008-01-31
The [uvcvideo module patch]("http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz") for isight includes both hardware IDs you are referring to, so i would guess they have both been around for awhile. In fact, on [this page]("http://www.mactel-linux.org/wiki/Lsusb") you can see that the 8300 ID seems to be on more Macs than 8501. I am assuming that there are two different camera manufacturers that Apple uses.

---

### Post by FunkyM on 2008-01-31
8300 is the iSight without firmware loaded.
Once the firmware is uploaded it connects as a new USB device 8501 and can be used as a video device.

Mac OSX does that automatically, on Linux you require a patched uvcvideo or the latest [udev loader tools]("http://bersace03.free.fr/ift/") alongside upstream [uvcvideo]("http://linux-uvc.berlios.de/").

---

### Post by bluec on 2008-02-01
Thanks to both of you. That makes sense now!

---

