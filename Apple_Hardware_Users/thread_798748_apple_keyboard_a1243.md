---
title: "apple keyboard a1243"
date: 2008-05-18
forum: Apple Hardware Users
---

### Post by giorgio-m on 2008-05-18
Hi I've got a PC (not apple), currently I'm using the Apple a1243 keyboard ([http://en.wikipedia.org/wiki/Apple_Keyboard](http://en.wikipedia.org/wiki/Apple_Keyboard)) on ubuntu 8.04, but it doesn't work. It worked perfectly under ubuntu 7.10, and it still works on the login screen, but once I login, only few keys keep working (for example the "k" prints a "2" etc).
The keyboard layout is "generic 105 international" with italian layout.

Thanks for any suggestion.

dmesg output when I disconnect and reconnect the keyboard
------------------------------------------
[ 1041.079825] usb 2-2: USB disconnect, address 7
[ 1041.079829] usb 2-2.2: USB disconnect, address 8
[ 1054.115966] usb 2-8: new high speed USB device using ehci_hcd and address 9
[ 1054.256814] usb 2-8: configuration #1 chosen from 1 choice
[ 1054.257052] hub 2-8:1.0: USB hub found
[ 1054.257161] hub 2-8:1.0: 3 ports detected
[ 1054.571455] usb 2-8.2: new low speed USB device using ehci_hcd and address 10
[ 1054.670172] usb 2-8.2: configuration #1 chosen from 1 choice
[ 1054.674029] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:02.1/usb2/2-8/2-8.2/2-8.2:1.0/input/input10
[ 1054.708481] input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:02.1-8.2
[ 1054.712951] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:02.1/usb2/2-8/2-8.2/2-8.2:1.1/input/input11
[ 1054.735249] input,hidraw2: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:02.1-8.2
------------------------------------------

---

### Post by Jammy4041 on 2008-05-18
Have you set the keyboard layout as a Mac Keyboard?

It should be Italian>>Mac Keyboard

---

### Post by giorgio-m on 2008-05-18
Hi I've tried all the keyboard layouts...

---

### Post by cyberdork33 on 2008-05-18
there is a bug in the linux kernel that recognizes the aluminum keyboards as the same keyboard as is in Macbooks. I is emulating a numpad in the main keyboard area like can be done on many laptops. I believe hitting F6 twice reverses this function. See bug report here:
[https://bugs.edge.launchpad.net/mactel-support/+bug/201887](https://bugs.edge.launchpad.net/mactel-support/+bug/201887)

---

### Post by giorgio-m on 2008-05-18
yeah, F6 twice and "thank you" ten times! :)

do you think that this bug needs to be submitted also somewhere else?

---

