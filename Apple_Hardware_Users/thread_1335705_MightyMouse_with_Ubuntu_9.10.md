---
title: "MightyMouse with Ubuntu 9.10"
date: 2009-11-23
forum: Apple Hardware Users
---

### Post by thinktyler on 2009-11-23
I'm getting connection refused when trying to pair my [old] mighty mouse with Ubuntu on MacbookPro 5,2.


tdhz77@tdhz77-laptop:~$ sudo hidd --search
Searching ...
	Connecting to device 00:23:DF:F4:B3:5E
Can't create HID control channel: Connection refused
tdhz77@tdhz77-laptop:~$ sudo gedit /etc/bluetooth/hcid.conf
tdhz77@tdhz77-laptop:~$ sudo hidd --search
Searching ...
	Connecting to device 00:23:DF:F4:B3:5E
Can't create HID control channel: Connection refused


hcid.conf 

device 00:23:DF:F4:B3:5E {
name "MightyMouse"
auth enable;
encrypt enable;
}


Please Help.

---

### Post by luigi.viggiano on 2009-11-24
Your computer must be always "discoverable" in bluetooth preferences. This made the difference with my mighty mouse.

---

### Post by thinktyler on 2009-11-24
> **luigi.viggiano said:**
> Your computer must be always "discoverable" in bluetooth preferences. This made the difference with my mighty mouse.

Made my laptop 'always discoverable' still no luck. Thanks though.

---

### Post by thinktyler on 2009-11-27
Bump...

---

### Post by hvthao on 2009-11-29
Try Blueman instead, then pair with the mouse. After restarting, it should work.

---

### Post by thinktyler on 2009-12-04
> **hvthao said:**
> Try Blueman instead, then pair with the mouse. After restarting, it should work.


Success! Thank you! 

SOLVED!

---

### Post by thinktyler on 2009-12-05
Make sure and hit the setup button after you start blueman "System>Preferences>Bluetooth Manager" 

then hit the setup button and hit "connnect to device" and you should be good.

---

