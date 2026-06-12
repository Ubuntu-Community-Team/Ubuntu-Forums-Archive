---
title: "[SOLVED] Camera not recognised"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-10-23
In Feisty, my camera (Nikon D40) was recognised immediately I connected via USB (without me having to do anything)

Following a clean install of Gutsy, this no longer happens. My MP3 player is recognised no probs, but camera isn't. In fact, I tried another digital camera and that was recognised too!

So, what has Gutsy got against my Nikon?!!

---

### Post by Martje_001 on 2007-10-24
Can you connect to your camera with f-spot?

---

### Post by qprfact on 2007-10-24
No, it doesn't see it

---

### Post by qprfact on 2007-10-24
Something is happening though - this is what dmesg says:

```
[46566.899613] usb 2-2: new high speed USB device using ehci_hcd and address 8
[46567.032663] usb 2-2: configuration #1 chosen from 1 choice
[46567.033039] scsi6 : SCSI emulation for USB Mass Storage devices
[46567.033329] usb-storage: device found at 8
[46567.033335] usb-storage: waiting for device to settle before scanning
[46572.029572] usb-storage: device scan complete
[46572.030554] scsi 6:0:0:0: Direct-Access     NIKON    D40              1.00 PQ: 0 ANSI: 2
[46572.035021] sd 6:0:0:0: [sdc] 4022273 512-byte hardware sectors (2059 MB)
[46572.035938] sd 6:0:0:0: [sdc] Write Protect is off
[46572.035950] sd 6:0:0:0: [sdc] Mode Sense: 0f 00 00 00
[46572.035956] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[46572.038512] sd 6:0:0:0: [sdc] 4022273 512-byte hardware sectors (2059 MB)
[46572.039179] sd 6:0:0:0: [sdc] Write Protect is off
[46572.039189] sd 6:0:0:0: [sdc] Mode Sense: 0f 00 00 00
[46572.039195] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[46572.039204]  sdc: sdc1

```

---

### Post by Martje_001 on 2007-10-24
Please report a bug.

---

### Post by qprfact on 2007-10-24
OK, will do!

---

### Post by qprfact on 2007-10-24
Looks like there are several bugs already! I found this one:

[https://bugs.launchpad.net/ubuntu/+bug/145153](https://bugs.launchpad.net/ubuntu/+bug/145153)

and this one:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134477](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134477)

The latter refers to a patch:

[http://launchpadlibrarian.net/9678067/unusual_devs.patch](http://launchpadlibrarian.net/9678067/unusual_devs.patch)

How do I apply this?

---

### Post by Martje_001 on 2007-10-24
> **qprfact said:**
>  [http://launchpadlibrarian.net/9678067/unusual_devs.patch](http://launchpadlibrarian.net/9678067/unusual_devs.patch)

How do I apply this?
That's not a patch... the patch is in the git of Nikon, I don't know much about that though :(

---

### Post by philinux on 2007-10-24
Try plugging camera in then launch Gthumb.

---

### Post by qprfact on 2007-10-24
gthumb doesn't do anything.

That isn't a patch then? 

Any other ideas?

---

### Post by philinux on 2007-10-24
I have to click File then import photos for my canon G5 to get mounted.

---

### Post by qprfact on 2007-10-24
Says "No camera detected"

---

### Post by philinux on 2007-10-24
Have you tried leaving it plugged in and then reboot.

you can can look at message.log to see what gives.

---

### Post by AgentXSmith on 2007-10-24
I'm having the same problem with my Olympus D-435.  Worked fine until I upgraded to Gutsy.  The gthumb app says I have an Olympus c-370 then tells me there are no photos to import (there are plenty on the camera) and the catalog doesn't show my model.  I've tried F stop and it says the same thing.  I've reported this and I'll be following this thread to see if they come up with a fix.

---

### Post by philinux on 2007-10-24
I have a feeling its the way the system recognises drives cos under Feisty my HD was always hda1 now its sda1 odd.

---

### Post by qprfact on 2007-10-24
I had the same hda to sda thing.

From the bug (and there were more than one relating to Nikons) I think it's a general issue that needs resolution

---

### Post by squashpup on 2007-10-24
Lots of people are having problems with this. In Kubuntu, I get an icon on the desktop when I plug my Panasonic Lumix DMC-FZ8, but clicking the icon does nothing.  Can't believe 7.10 got out the door with this not working.

---

### Post by qprfact on 2007-10-26
Following on from the bug report I mentioned a couple of posts earlier, I was directed to Nikon themselves for a firmware upgrade - [http://www.nikon-euro.com/kdb/en/2007/20687/D40_win_en.html](http://www.nikon-euro.com/kdb/en/2007/20687/D40_win_en.html)

It needs to be done in Windows, and requires the memory card to be formatted first (so you get a lovely Catch 22 of wanting to save the files to a PC, but can't do so before the firmware patch is applied, which will delete the files!)

Luckily I have dual boot, so I can copy the pics first and try it.

I'll post back and say if it worked!

---

### Post by qprfact on 2007-10-27
It worked! All operating as it should do now....

---

### Post by Rustafur on 2008-06-23
I just purchased a Nikon D40, and it came stock with the v1.1 firmware. And it's worth mentioning that you apparently do need the v1.1 firmware installed AND you need to swtich your USB mode in the menu from Mass Storage to PTP. It's much much slower that mass storgage though :( Please please can we get this problem worked out to be able to use Mass Storage USB transfer on such a popular camera?

---

