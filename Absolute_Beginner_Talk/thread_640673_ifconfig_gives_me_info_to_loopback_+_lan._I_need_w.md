---
title: "ifconfig gives me info to loopback + lan. I need wlan..."
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-12-14
I need to find out the mac address to my internal wlan adapter, however it doesn't seem to pick it up when I run ifconfig. It just shows me the loopback and wired lan.

---

### Post by mcduck on 2007-12-14
Try with "ifconfig -a".

---

### Post by deepank on 2007-12-14
I think you do not have the drivers for your Wireless ... I suggest you to look for your drivers .

---

### Post by Roasted on 2007-12-14
How would that matter? 
-a switch didn't work.

---

### Post by ctyc on 2007-12-14
ifconfig -a will show all currently available interfaces.
Here is what happens on my laptop when I run ifconfig -s with wireless OFF then again with wireless ON:

sudo ifconfig -s
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR   TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1500 0     53064      0      0      0    43057      0      0      0 BMRU
lo    16436 0        24      0      0      0       24      0      0      0 LRU
dbl@lappylaptop:~$ sudo ifconfig -s
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR   TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1500 0     53261      0      0      0    43171      0      0      0 BMRU
eth1   1500 0         0      0      9      0        0      0      0      0 BMU
lo    16436 0        24      0      0      0       24      0      0      0 LRU

As you can see with wireless ON eth1 is now available so that ifconfig -a will display the HWaddr.

---

### Post by Roasted on 2007-12-14
I don't believe my internal WLAN NIC is supported by Gutsy, hence this issue.

If I do an ifconfig with it turned on, it doesn't pick it up.
If I do an ifconfig with the usb wireless adapter plugged in, it sees it right away and lists it.

Guess that's why.

---

