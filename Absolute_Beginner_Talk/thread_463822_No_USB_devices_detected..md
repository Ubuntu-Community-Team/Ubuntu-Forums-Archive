---
title: "No USB devices detected."
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by ajinkya_naik on 2007-06-04
Hi, I am very new to Ubuntu. I have installed 7.04 from the Live CD . The problem is that Ubuntu does not detect any of my USB devices. I used usbutils in terminal as a website recommended, but it returned no result. My motherboard is P4MAM-V from MSI. Does Ubuntu support this motherboard? Please help!

---

### Post by daimaru on 2007-06-04
what does 
```
lsusb
```
give you ? do your devices show up? 
unplug your usb device, open terminal enter
```
sudo tail -f /var/log/messages
```
now plug in your usb device and check if they get registered.
edit: just watch the last few lines and see if anything new shows up. this is no fix just to get some information.

---

### Post by daimaru on 2007-06-04
please post the output of those commands. if you want to copy stuff from the console just highlight it with your mouse. -- to paste hit the middle mouse button.

---

### Post by ajinkya_naik on 2007-06-05
The first command lsusb gave no output at all.

Then I unplugged the devices, gave the second command.
The second one prompted my password, and then displayed the following:
Jun  5 17:34:27 naiks-desktop dhcdbd: Unrequested down ?:3
Jun  5 17:35:03 naiks-desktop gconfd (naiks-5090): starting (version 2.18.0.1), pid 5090 user 'naiks'
Jun  5 17:35:03 naiks-desktop gconfd (naiks-5090): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun  5 17:35:03 naiks-desktop gconfd (naiks-5090): Resolved address "xml:readwrite:/home/naiks/.gconf" to a writable configuration source at position 1
Jun  5 17:35:03 naiks-desktop gconfd (naiks-5090): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  5 17:35:03 naiks-desktop gconfd (naiks-5090): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun  5 17:35:03 naiks-desktop gconfd (naiks-5090): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun  5 17:35:09 naiks-desktop gconfd (naiks-5090): Resolved address "xml:readwrite:/home/naiks/.gconf" to a writable configuration source at position 0
Jun  5 17:53:49 naiks-desktop -- MARK --
Jun  5 18:13:50 naiks-desktop -- MARK -



When I plugged in the USB devices, it added no new output at the terminal.

I had used lsusb before as well, and it had yielded no result during that time as well. 

Is there a hardware problem?

---

