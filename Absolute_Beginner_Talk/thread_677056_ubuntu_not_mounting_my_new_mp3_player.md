---
title: "ubuntu not mounting my new mp3 player"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by malathion on 2008-01-24
I just got  new Centon 2gb usb mp3 player. Here's what happens in dmesg when I plug it in that looks relevant:

> [55829.661227] usb-storage: device found at 2
[55829.661230] usb-storage: waiting for device to settle before scanning
[55829.661345] usbcore: registered new interface driver usb-storage
[55829.661405] USB Mass Storage support registered.
[55834.659759] usb-storage: device scan complete
[55834.660377] scsi 10:0:0:0: Direct-Access              Audio Player          PQ: 0 ANSI: 0 CCS
[55834.661609] sd 10:0:0:0: [sde] 4016640 512-byte hardware sectors (2057 MB)
[55834.666092] sd 10:0:0:0: [sde] Write Protect is off
[55834.666098] sd 10:0:0:0: [sde] Mode Sense: 3b 00 00 00
[55834.666101] sd 10:0:0:0: [sde] Assuming drive cache: write through
[55834.671361] sd 10:0:0:0: [sde] 4016640 512-byte hardware sectors (2057 MB)
[55834.671982] sd 10:0:0:0: [sde] Write Protect is off
[55834.671985] sd 10:0:0:0: [sde] Mode Sense: 3b 00 00 00
[55834.671988] sd 10:0:0:0: [sde] Assuming drive cache: write through
[55834.671993]  sde: sde1
[55834.672866]  sde: p1 exceeds device capacity
[55834.672939] sd 10:0:0:0: [sde] Attached SCSI removable disk
[55834.672986] sd 10:0:0:0: Attached scsi generic sg5 type 0
[55834.868090] attempt to access beyond end of device
[55834.868096] sde: rw=0, want=4021032, limit=4016640
[55834.868101] Buffer I/O error on device sde1, logical block 502624
[55834.868106] attempt to access beyond end of device
[55834.868108] sde: rw=0, want=4021032, limit=4016640
[55834.868111] Buffer I/O error on device sde1, logical block 502624
[55834.868118] attempt to access beyond end of device
[55834.868121] sde: rw=0, want=4021240, limit=4016640
[55834.868123] Buffer I/O error on device sde1, logical block 502650
[55834.868126] attempt to access beyond end of device
[55834.868129] sde: rw=0, want=4021240, limit=4016640
[55834.868131] Buffer I/O error on device sde1, logical block 502650
[55834.869877] attempt to access beyond end of device
[55834.869882] sde: rw=0, want=4021248, limit=4016640
[55834.869886] Buffer I/O error on device sde1, logical block 502651
[55834.869891] attempt to access beyond end of device
[55834.869894] sde: rw=0, want=4021248, limit=4016640
[55834.869897] Buffer I/O error on device sde1, logical block 502651
[55834.869908] attempt to access beyond end of device
[55834.869911] sde: rw=0, want=4021248, limit=4016640
[55834.869914] Buffer I/O error on device sde1, logical block 502651
[55834.869921] attempt to access beyond end of device
[55834.869924] sde: rw=0, want=4021248, limit=4016640
[55834.869928] Buffer I/O error on device sde1, logical block 502651
[55834.869934] attempt to access beyond end of device
[55834.869937] sde: rw=0, want=4021248, limit=4016640
[55834.869940] Buffer I/O error on device sde1, logical block 502651
[55834.869947] attempt to access beyond end of device
[55834.869950] sde: rw=0, want=4021248, limit=4016640
[55834.869954] Buffer I/O error on device sde1, logical block 502651
[55834.869960] attempt to access beyond end of device
[55834.869964] sde: rw=0, want=4021248, limit=4016640
[55834.869972] attempt to access beyond end of device
[55834.869975] sde: rw=0, want=4021192, limit=4016640
[55834.869994] attempt to access beyond end of device
[55834.869997] sde: rw=0, want=4021240, limit=4016640
[55834.870004] attempt to access beyond end of device
[55834.870007] sde: rw=0, want=4021248, limit=4016640
[55834.870014] attempt to access beyond end of device
[55834.870017] sde: rw=0, want=4021248, limit=4016640
[55834.922583] attempt to access beyond end of device
[55834.922589] sde: rw=0, want=4021032, limit=4016640
[55834.922593] attempt to access beyond end of device
[55834.922596] sde: rw=0, want=4021032, limit=4016640
[55834.922603] attempt to access beyond end of device
[55834.922606] sde: rw=0, want=4021240, limit=4016640
[55834.922609] attempt to access beyond end of device
[55834.922611] sde: rw=0, want=4021240, limit=4016640
[55834.930086] attempt to access beyond end of device
[55834.930093] sde: rw=0, want=4021248, limit=4016640
[55834.930104] attempt to access beyond end of device
[55834.930106] sde: rw=0, want=4021248, limit=4016640
[55834.930112] attempt to access beyond end of device
[55834.930115] sde: rw=0, want=4021248, limit=4016640
[55834.930123] attempt to access beyond end of device
[55834.930126] sde: rw=0, want=4021248, limit=4016640
[55834.930130] attempt to access beyond end of device
[55834.930132] sde: rw=0, want=4021248, limit=4016640
[55834.930137] attempt to access beyond end of device
[55834.930139] sde: rw=0, want=4021248, limit=4016640
[55834.930144] attempt to access beyond end of device
[55834.930146] sde: rw=0, want=4021248, limit=4016640
[55834.930290] attempt to access beyond end of device
[55834.930293] sde: rw=0, want=4021192, limit=4016640
[55834.930301] attempt to access beyond end of device
[55834.930303] sde: rw=0, want=4021240, limit=4016640
[55834.930308] attempt to access beyond end of device
[55834.930311] sde: rw=0, want=4021248, limit=4016640
[55834.930316] attempt to access beyond end of device
[55834.930318] sde: rw=0, want=4021248, limit=4016640


Can anyone decipher for me what is happening?

---

### Post by stchman on 2008-01-24
I have a SanDisk player and if I switch the USB mode to MSC Ubuntu auto mounts it just fine.  You may try something similar.

---

### Post by malathion on 2008-01-24
> **stchman said:**
> I have a SanDisk player and if I switch the USB mode to MSC Ubuntu auto mounts it just fine.  You may try something similar.

Sounds interesting, but where is this setting? Thanks

---

### Post by stchman on 2008-01-24
> **malathion said:**
> Sounds interesting, but where is this setting? Thanks

I know where the setting is on the Sandisk players but who knows if there is such a setting on your player.

I purposely bought that player because it has excellent compatibility with Linux.  The iPod while being the industry leader has spotty Linux support.

I just wanted a player that I can plug in and a removable drive icon pops up.  I can then drag and drop my MP3s into the appropriate folder.

---

### Post by lespaul_rentals on 2008-01-24
> **stchman said:**
> I know where the setting is on the Sandisk players but who knows if there is such a setting on your player.

I purposely bought that player because it has excellent compatibility with Linux.  The iPod while being the industry leader has spotty Linux support.

I just wanted a player that I can plug in and a removable drive icon pops up.  I can then drag and drop my MP3s into the appropriate folder.

Sandisk is great, they are very nice to Linux and aren't like Apple, who try to lock you in to their proprietary crap.  :guitar:

---

### Post by jeffus_il on 2008-01-24
From a Wiki:
[http://en.wikibooks.org/wiki/Sandisk_Sansa_MP3_players/m200#Changing_USB_mode](http://en.wikibooks.org/wiki/Sandisk_Sansa_MP3_players/m200#Changing_USB_mode)
> **Changing USB mode**

 If you want to set your player to USB Mass Storage mode, try this:
Menu button - Settings - USB - MSC
There might be a difference in firmware versions (Europe and USA have different firmware), so check if yours is the same.
 The Americas Version(Usa) has a higher volume setting and Fm reception while the E(Europe version) Has no Fm reception and has a volume Cap On It.


---

### Post by malathion on 2008-01-24
> **jeffus_il said:**
> From a Wiki:
[http://en.wikibooks.org/wiki/Sandisk_Sansa_MP3_players/m200#Changing_USB_mode](http://en.wikibooks.org/wiki/Sandisk_Sansa_MP3_players/m200#Changing_USB_mode)

This looks cool, except my player is made by Centon, not Sandisk. Is there no way to get it to work with unbuntu unless it's made by Sandisk? :(

---

### Post by jeffus_il on 2008-01-24
Use the Menu to try to find settings that will give you the option of setting MSC mode.

---

