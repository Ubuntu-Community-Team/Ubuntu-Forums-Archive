---
title: "Server edition fix for iSight camera"
date: 2011-09-09
forum: Apple Hardware Users
---

### Post by seranow on 2011-09-09
**Symptoms**

[LIST]
[*]The builtin iSight in Macbooks have driver issues. They cause warnings that will popup constantly throughout the console: "*[ 600.264462] hub 1-0:1.0: unable to enumerate USB device on port 1*.

[*]This directly causing a direct impact on the serverload. 

[*]Impossible 'clear view' in your console
[/LIST]

**Previous Solutions:**
You are able to extract the drivers from your Mac OS X install cd with a small program. Information about this can be found at: [https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight)

However, since we are running a server edition, I'm assuming that you will not be using that iSight in the first place. I found it easier to unbind the driver, which solves the problem and their is no need to have a Mac OS X cd. 

**Proposed fix:**

```
sudo su
```
```
apt-get install tree
```

Execute the following command to find your iSight device number
```
for device in $(ls /sys/bus/usb/devices/*/product); do echo $device;cat $device;done
```

It will output something like this (my iSight is not in the list anymore since I've worked around it already)
```
root@poseidon:/sys/bus/usb/devices# for device in $(ls /sys/bus/usb/devices/*/product); do echo $device;cat $device;done
/sys/bus/usb/devices/2-2/product
Apple Internal Keyboard / Trackpad
/sys/bus/usb/devices/4-2/product
IR Receiver
/sys/bus/usb/devices/usb1/product
EHCI Host Controller
/sys/bus/usb/devices/usb2/product
UHCI Host Controller
/sys/bus/usb/devices/usb3/product
UHCI Host Controller
/sys/bus/usb/devices/usb4/product
UHCI Host Controller
/sys/bus/usb/devices/usb5/product

```

As you can see in the locations that after /devices/ you see a number. Remember the one from your iSight. It will be something like this 1-0:1.0

Now Ubuntu has a driver attached to the iSight hub that is malfunctioning. Our intent is to unbind that driver from the device so it won't give an error. 

First we need to see if that driver is active. Perform the following command and look for the driver symlink. Change the device number to your findings from the previous step. 
```
tree /sys/bus/usb/devices/1-0:1.0
```

driver -> ../../../../../../bus/usb/drivers/**hub**
The hub is the device where the iSight is hooked onto. That's where we are going to send our final command to. 

```
echo -n "1-0:1.0" > /sys/bus/usb/drivers/hub/unbind
```

The problem should be resolved now. This will immediatly result in the loads to drop and the error messages will stop filling the console. 

However this fix will be undone upon reboot. 
You can put the previous command in /etc/rc.local and the problem will stay away.

Edit: This way of working is only compatible from the 2.6.13-rc3 kernel and up.

---

