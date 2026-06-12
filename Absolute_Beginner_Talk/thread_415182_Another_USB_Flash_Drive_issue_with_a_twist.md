---
title: "Another USB Flash Drive issue with a twist"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Lonestar on 2007-04-20
I have seen several posts about USB flash drive sticks not being mounted.  I bought a Kingston DataTraveler 2 GB drive yesterday.  My old small Lexar 64 MB drive, when plugged in, mounts in about 10 seconds, but I could not get the Kingston USB drive to mount.  I then plugged in the Kingston drive and  got distracted but later saw the drive pop up on the screen.  I tried this several times and it takes about **16 minutes** to mount!!!

Why is this happening?  :confused: 

I went into System Log, then Messages - I am not going to paste in the entire log but here is an excerpt where you can get an idea what is going on.  I would really like to get some feedback from the power users on what is going on!  

Thank you.

[INDENT]Apr 20 08:54:33 ecs-laptop kernel: [17187776.696000] usb 1-1: new full speed USB device using uhci_hcd and address 88

***-----gap where more of the above and below took place with different addresses --------***

Apr 20 09:09:35 ecs-laptop kernel: [17188678.604000] usb 1-1: new full speed USB device using uhci_hcd and address 71
Apr 20 09:09:59 ecs-laptop kernel: [17188704.308000] usb 1-1: new full speed USB device using uhci_hcd and address 46
Apr 20 09:10:06 ecs-laptop kernel: [17188711.364000] usb 1-1: new full speed USB device using uhci_hcd and address 73
Apr 20 09:10:17 ecs-laptop kernel: [17188721.748000] usb 1-1: new full speed USB device using uhci_hcd and address 113
Apr 20 09:10:17 ecs-laptop kernel: [17188721.912000] usb 1-1: configuration #1 chosen from 1 choice
Apr 20 09:10:17 ecs-laptop kernel: [17188722.284000] usbcore: registered new driver libusual
Apr 20 09:10:17 ecs-laptop kernel: [17188722.364000] SCSI subsystem initialized
Apr 20 09:10:17 ecs-laptop kernel: [17188722.372000] Initializing USB Mass Storage driver...
Apr 20 09:10:17 ecs-laptop kernel: [17188722.376000] scsi0 : SCSI emulation for USB Mass Storage devices
Apr 20 09:10:17 ecs-laptop kernel: [17188722.376000] usbcore: registered new driver usb-storage
Apr 20 09:10:17 ecs-laptop kernel: [17188722.376000] USB Mass Storage support registered.
Apr 20 09:10:22 ecs-laptop kernel: [17188727.380000]   Vendor:           Model: USB Flash Memory  Rev: 6.50
Apr 20 09:10:22 ecs-laptop kernel: [17188727.380000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr 20 09:10:22 ecs-laptop kernel: [17188727.548000] SCSI device sda: 3903487 512-byte hdwr sectors (1999 MB)
Apr 20 09:10:22 ecs-laptop kernel: [17188727.552000] sda: Write Protect is off
Apr 20 09:10:22 ecs-laptop kernel: [17188727.560000] SCSI device sda: 3903487 512-byte hdwr sectors (1999 MB)
Apr 20 09:10:22 ecs-laptop kernel: [17188727.564000] sda: Write Protect is off
Apr 20 09:10:22 ecs-laptop kernel: [17188727.564000]  sda: sda1
Apr 20 09:10:23 ecs-laptop kernel: [17188727.584000] sd 0:0:0:0: Attached scsi removable disk sda
Apr 20 09:10:23 ecs-laptop kernel: [17188727.640000] sd 0:0:0:0: Attached scsi generic sg0 type 0[/INDENT]

---

### Post by LaRoza on 2007-04-20
I am not sure why it is taking so long, but are there any programs installed on the flash drive?

I always format my flash drives when I get them, including the Kingston Data Traveler, so anything on them is wiped.

---

### Post by Lonestar on 2007-04-20
Howdy, and thanks for the reply.  I saw other posts about programs on the drive, it came with no programs, no U3, I did reformat the drive. 

I have tried this a few more times and get the same result, the drive will eventually mount but it takes 15+ minutes most of the time.

---

### Post by Lonestar on 2007-04-21
Has anyone with USB Drive problems seen this in the message log?

---

### Post by shof2k on 2007-04-24
> **Lonestar said:**
> Has anyone with USB Drive problems seen this in the message log?

I'm getting the message ```
usb 1-1: configuration #1 chosen from 1 choice
```.  Searching around showed this thread [http://ubuntuforums.org/showthread.php?t=303259&highlight=usb+card+reader](http://ubuntuforums.org/showthread.php?t=303259&highlight=usb+card+reader).

This suggests some sort of power issue.  I'm using a laptop with a USB wireless dongle and a USB card reader.  If I pull the dongle out then the card reader or USB drive works ok, so it sounds like a USB power issue.

Hope the kernel devs can fix this soon as it is annoying.

....now to find out why my desktop keeps stuttering.

---

