---
title: "Syncing with Palm Treo PDA"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by cjeness on 2008-01-16
I am trying to do the initial set up of my Palm Treo 650 with the latest version of Ubuntu Gutsey Gibbon using JPilot.   In the past, I have successfully sync'd this device with KPilot running under Suse 9.3.

When I initially plug in my Treo 650 to the USB port and press the sync button, I see the messages:

Jan 15 23:53:54 yorkie kernel: [307621.340000] usb 2-2: new full speed USB device using uhci_hcd and address 7
Jan 15 23:53:54 yorkie kernel: [307621.512000] usb 2-2: configuration #1 chosen from 1 choice
Jan 15 23:53:54 yorkie kernel: [307621.516000] visor 2-2:1.0: Handspring Visor / Palm OS converter detected
Jan 15 23:53:54 yorkie kernel: [307621.516000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jan 15 23:53:54 yorkie kernel: [307621.516000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB1

I then run the Gnome Pilot configuration.   I use "usb" for the "Type" and I have tried every possible Device.  Nothing happens and eventually the Treo device gives up and disconnects.   I have looked at various Ubuntu help documents; however, it was difficult to tell what changes were actually necessary.   For example, it was noted that a certain line needed to be added to the XML file; however, this line was already present.

Any help would be greatly appreciated.

---

### Post by cjeness on 2008-01-16
I finally got the sync working by doing the following:

1.  Set up a rule in /etc/udev/rules.d/10-custom.rules

BUS="usb", SYSFS{product}="*Palm*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot
", MODE="666"

2.  Restarted udev:

/etc/init.d/udev restart

3.  Previously, I had added visor as the last line of /etc/modules and then "sudo modprobe visor" to force the module to load.

4.  Then I started the sync on the Palm PDA and waited until I saw the ttyUSB0 and ttyUSB1 set up in "/var/log/messages".

5.  Finally, I started the Palm Devices configuration tool and the setup proceeded correctly using "/dev/pilot" as the device.

The differences between the successful attempt and the failed attempt was using "*Palm*" for the SYSFS{product} in the custom rule rather than "Palm Handheld*" and also starting the sync on the Palm device first.  So the good news is that it seems to work.   The bad news is that the setup process is somewhat difficult.

---

