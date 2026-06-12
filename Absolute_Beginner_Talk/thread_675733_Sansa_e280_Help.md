---
title: "Sansa e280 Help"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Oro_07 on 2008-01-23
I just bought a SanDisk Sansa e280 mp3 player. I am running Gutsy 7.10 by the way ... i connected  the mp3 player to the usb hub and nothing happened and ubuntu wasnt detecting it.

Can someone help me step by step on how to get it to work?

---

### Post by jeffus_il on 2008-01-23
The first step is to remove and replace the USB connecter and the type ```
dmesg
``` in a terminal to to if your computer "sees" the device, look at the last few lines , you will see if the Sansa is there.

---

### Post by Oro_07 on 2008-01-23
[ 2975.692000] usbcore: registered new interface driver usb-storage
[ 2975.692000] USB Mass Storage support registered.
[ 2980.692000] usb-storage: device scan complete
[ 2986.304000] usb 5-3: reset high speed USB device using ehci_hcd and address 4
[ 2996.548000] usb 5-3: reset high speed USB device using ehci_hcd and address 4
[ 2996.908000] scsi 2:0:0:0: scsi: Device offlined - not ready after error recovery
[ 2996.908000] usb 5-3: USB disconnect, address 4


thats what it is showing on the last lines

---

### Post by jeffus_il on 2008-01-23
There are lots of threads on the Sansa, You may have to format it of or to switch mode. I guess the mode to MSC thing might be your solution. Your device is seen by Ubuntu, but it seems to fail to read the filesystem, so it could be mode.

Read these:
[http://ubuntuforums.org/showthread.php?t=645514&highlight=sansa+e280](http://ubuntuforums.org/showthread.php?t=645514&highlight=sansa+e280)
[http://ubuntuforums.org/showthread.php?t=312196&highlight=sansa+e280](http://ubuntuforums.org/showthread.php?t=312196&highlight=sansa+e280)

---

### Post by Oro_07 on 2008-01-23
sweet thanks. i got Sansa to pop up on my desktop and ubuntu i guess regognized it.

Now i wonder if i just drag my music into the music folder of sansa file

---

### Post by stchman on 2008-01-23
> **Oro_07 said:**
> I just bought a SanDisk Sansa e280 mp3 player. I am running Gutsy 7.10 by the way ... i connected  the mp3 player to the usb hub and nothing happened and ubuntu wasnt detecting it.

Can someone help me step by step on how to get it to work?

Change the USB mode to MSC.  This will allow Linux to see the player as a drive.

---

