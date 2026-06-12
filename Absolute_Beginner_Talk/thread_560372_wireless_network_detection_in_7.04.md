---
title: "wireless network detection in 7.04"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by demoncleaner on 2007-09-26
Hi, I have tried Ubuntu 7.04 for the first time yesterday and found it to be promising.
It did detect my wireless network (BT Voyager 1290, 64bit HEX)but after clicking on it and adding the network password it could not connect.
Why could that be?:confused:
Thanks.

Chris

---

### Post by Niniel on 2007-09-26
Speaking of which - does Ubuntu support only WEP? At least the live-CD won't let me select WPA for encryption. Will the full installation?

---

### Post by Austin_KW on 2007-09-26
The important thing is your wireless adapter on the PC, not the Voyager.

We need to know your adapter type, so what is the output of the following terminal commands
```
lspci
lsusb
```

Ubuntu does suport WPA, how will depend on your adapter and the driver.

---

### Post by mikewhatever on 2007-09-26
> **Niniel said:**
> Speaking of which - does Ubuntu support only WEP? At least the live-CD won't let me select WPA for encryption. Will the full installation?

There seems to be no option for WPA in System>Admin>Network, but if you click on the network manager icon next to the clock and chose 'Connect to other wireless...', then there are options for both wpa and wpa2.

---

### Post by Austin_KW on 2007-09-26
You will not be offered the WPA options if you are trying to connect to a WEP network, would not make sense?

---

### Post by Niniel on 2007-09-26
Oh, ok, thanks for pointing me in the right direction.

---

### Post by Niniel on 2007-09-26
> **Austin_KW said:**
> You will not be offered the WPA options if you are trying to connect to a WEP network, would not make sense?

Yes, Austin, that would make sense. 
Trouble is, I use WPA. 

But Mike already helped me out, so all is/shall be well.

---

### Post by demoncleaner on 2007-09-26
lsusb returns: Bus005 Device 003: ID 07d1:3c03 D-Link System (my usb connected wireless adapter)

---

### Post by Austin_KW on 2007-09-26
Ok google suggest that the chipset is one of the ralinks, rt2500usb or rt73.

To be sure which can you use a fingernail in the usb dongle's seam and pop it open. Post the chip id/number back here.  
I think it is probably an rt73 (newer) so you would follow this howto post [http://ubuntuforums.org/showthread.php?t=400236&goto=newpost](http://ubuntuforums.org/showthread.php?t=400236&goto=newpost).

---

### Post by mikewhatever on 2007-09-26
> **Austin_KW said:**
> You will not be offered the WPA options if you are trying to connect to a WEP network, would not make sense?

No, it's not that smart. There are several networks around here, both wap and wep protected, and the options remain the same.

---

