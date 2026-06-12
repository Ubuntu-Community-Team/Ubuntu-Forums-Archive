---
title: "No USB entry in /proc/acpi/wakeup"
date: 2011-08-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Mortenterstrup on 2011-08-07
I need to be able to resume from suspend on my eee-pc 901, activated by a usb mouse. When looking through various help pages, they all mention setting USB entries in the /proc/acpi/wakeup file to enabled. But the contents of that file is only:
P0P2 S4 disabled
P0P1 S4 disabled
etc.
 
Ie. no USB - only these P0P ones. I have tried all various kinds of Ubunto (easypeasy, ubunto 10.04, eeebuntu 3.0, mythbuntu). They all show the same 'phenonmenon'.
 
Anyone has an idea ?

---

### Post by fdrake on 2011-08-07
> **Mortenterstrup said:**
> I need to be able to resume from suspend on my eee-pc 901, activated by a usb mouse. When looking through various help pages, they all mention setting USB entries in the /proc/acpi/wakeup file to enabled. But the contents of that file is only:
P0P2 S4 disabled
P0P1 S4 disabled
etc.
 
Ie. no USB - only these P0P ones. I have tried all various kinds of Ubunto (easypeasy, ubunto 10.04, eeebuntu 3.0, mythbuntu). They all show the same 'phenonmenon'.
 
Anyone has an idea ?
did you try:
```
sudo -s
echo USB > /proc/acpi/wakeup
echo USB2 > /proc/acpi/wakeup
```

source:[http://ubuntuforums.org/showthread.php?t=1642817](http://ubuntuforums.org/showthread.php?t=1642817)

---

### Post by Mortenterstrup on 2011-08-07
> **fdrake said:**
> did you try:
```
sudo -s
echo USB > /proc/acpi/wakeup
echo USB2 > /proc/acpi/wakeup
```
 
source:[http://ubuntuforums.org/showthread.php?t=1642817](http://ubuntuforums.org/showthread.php?t=1642817)
 
Yes. But there are no USB entries in that file  (only P0Px). I have tried to do as you suggested anyway, but still there are no lines in the file mentioning USB, and no change the resume function.

---

### Post by fdrake on 2011-08-07
> **Mortenterstrup said:**
> Yes. But there are no USB entries in that file  (only P0Px). I have tried to do as you suggested anyway, but still there are no lines in the file mentioning USB, and no change the resume function.

can u post your lsusb?

---

### Post by Mortenterstrup on 2011-08-07
Thanks; sure:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 003: ID 059b:047a Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by bunghole23 on 2011-09-15
Greetings,

I ran into the same problem just an hour ago. Not shure if it helps your case, but this is how I solved it:

1. Look up 'lsusb' to check which bus your remote device is connected to. According to your last post, it should Bus 002.

2. In Case it is, look out for this file: /sys/bus/usb/devices/usb2/2-**X**/power/wakeup
**Note:** The 'X' might be a '1' or a '2' or maybe even higher - it depends. 
If it isn't, go change the two number in '[...]/usb2/2-[...]' to the bus where your device is attached to.

3. Edit the file and you will see that it has a 'disabled' in it. Make that 'enabled'. 
Send your pc into suspend and try waking it up again via the usb device. It should work now. 

4. In case it worked, make the change persistent by adding the following line to your /etc/rc.local: 

echo "enabled" > /sys/bus/usb/devices/usb2/2-**X**/power/wakeup

Hope it will work! :)

---

