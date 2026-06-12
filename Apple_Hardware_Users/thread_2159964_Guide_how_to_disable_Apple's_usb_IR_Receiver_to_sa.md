---
title: "Guide: how to disable Apple's usb IR Receiver to save battery"
date: 2013-07-05
forum: Apple Hardware Users
---

### Post by michelino80 on 2013-07-05
Hi,
If you're not using the IR Receiver on your MacBook (Pro) under Ubuntu, then you want to disable it to save ~1.5W of battery drainage. 
Here is how, tested on Ubuntu 12.04 32bit, kernel 3.4.48, MacBook Pro 15" 8,2:

1) Open a terminal
2) run:
for device in $(ls /sys/bus/usb/devices/*/product); do echo -n $device " ";cat $device;done
3) look for the line containing "IR Receiver", in my case:
/sys/bus/usb/devices/2-1.1/product  IR Receiver
The string you need from this step is "2-1.1"
4) sudo emacs /etc/rc.local
5) add this line right before "exit 0", repacing "2-1.1" with whatever you found in step 3):
echo "2-1.1" |tee /sys/bus/usb/drivers/usb/unbind
6) save and reboot

This should work on kernels > 2.6, as the power saving strategy has changed since then. 
Please comment to this post if you are aware of necessary modifications to make it work on other models / versions / bla bla..

cheers!
mic

---

