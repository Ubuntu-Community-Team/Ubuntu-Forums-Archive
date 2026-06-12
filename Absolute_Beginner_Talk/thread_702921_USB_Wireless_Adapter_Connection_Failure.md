---
title: "USB Wireless Adapter Connection Failure"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by tomsr on 2008-02-20
I am a beginner with Linux and Ubuntu 7.10. I successfully installed the OS on an older computer and it connects to the Internet just fine when wired to my Netgear Cable Modem/Router. My problem is that I cannot connect via Linksys Wireless-G USB Adapter, model WUSB54G v.4. I am asked for my network passphrase over and over again.

The Network Monitor shows my local network and a couple of neighborhood home networks so the adapter appears to be working. I have a WEP security code set on my router. When I type in that code or the passphrase it is unable to connect.

I have had blue bars appear on the panel but no connection. Can anyone help me with this problem. I hope I explained it well enough.

Thanks,
Tom

---

### Post by Austin_KW on 2008-02-20
I think that adapter has a ralink chipset either a rt2570 or a rt73.

The driver inclued with ubuntu is the new beta driver. 
Look at the using the legacy driver from serialmonkey.com. It will not work with network manager but it will be much more stable.

Have a read through the first post in this thread. [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
This is for the the rt73 but it will be similar for the rt2570

---

### Post by tomsr on 2008-02-21
Thanks much. I'll check out your suggestions.
Tom

---

### Post by tomsr on 2008-02-21
I got the driver from serialmonkey. Now, how do I get it installed? Sorry I so dumb with Linux.

---

### Post by Austin_KW on 2008-02-21
You will need to check which serialmonkey driver you need. The last time I saw one of these adapters it was the rt2570 but that is an older chipset.

if you type the command 
```
lsmod | grep usbcore
``` you should see what usb drivers are loaded.

If you see rt73usb then it is a rt73 device
If you see rt2500usb then it is an rt2570
If you see both then you it could be either driver.

Get the appropriate legacy CVS driver from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads) (not the rt2x00 as that is the beta driver that you are currently running).
Build the legacy driver, remove and blacklist the current driver  and then configure as per first post in [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

