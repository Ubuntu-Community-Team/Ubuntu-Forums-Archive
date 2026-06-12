---
title: "Get Ubuntu to recognize Mymusix PD-6070"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by DVD-R on 2008-01-30
Hi Gang,
I just picked up a new Mymusix PD-6070 mp3 player.
Plugged it into the laptop (Ubuntu 7.10 - the Gutsy Gibbon - released in October 2007)
The unit does not know anything got plugged in.
My Lexar thumb drive is recognized with no problem.

Anyone deal with this one?

Thanks!

---

### Post by dcstar on 2008-01-31
> **DVD-R said:**
> Hi Gang,
I just picked up a new Mymusix PD-6070 mp3 player.
Plugged it into the laptop (Ubuntu 7.10 - the Gutsy Gibbon - released in October 2007)
The unit does not know anything got plugged in.
My Lexar thumb drive is recognized with no problem.

Anyone deal with this one?

Thanks!

Post the output of the **dmesg** command when you plug the device in.

---

### Post by T_W on 2008-04-05
I don't know if the OP is out their somewhere, but for future generations:

I haven't found an automated way to do this, but I was able to mount the player by typing in the command

$ pmount /dev/sdb1

This mounted the player under /meda/sdb1.

I was then able to drag songs to the player.

To unmount, I had to do a:

 sudo umount /media/sdb1

In my case, /dev/sdb1 was the device reported by dmesg

```
Apr  5 09:49:21 localhost kernel: [221716.353640] Initializing USB Mass Storage driver...
Apr  5 09:49:21 localhost kernel: [221716.353712] scsi4 : SCSI emulation for USB Mass Storage devices
Apr  5 09:49:21 localhost kernel: [221716.353781] usbcore: registered new interface driver usb-storage
Apr  5 09:49:21 localhost kernel: [221716.353784] USB Mass Storage support registered.
Apr  5 09:49:26 localhost kernel: [221721.346064] scsi 4:0:0:0: Direct-Access     Generic  Audio Player     0100 PQ: 0 ANSI: 4
Apr  5 09:49:26 localhost kernel: [221721.347415] sd 4:0:0:0: [sdb] 484224 2048-byte hardware sectors (992 MB)
Apr  5 09:49:26 localhost kernel: [221721.348038] sd 4:0:0:0: [sdb] Write Protect is off
Apr  5 09:49:26 localhost kernel: [221721.355527] sd 4:0:0:0: [sdb] 484224 2048-byte hardware sectors (992 MB)
Apr  5 09:49:26 localhost kernel: [221721.356149] sd 4:0:0:0: [sdb] Write Protect is off
Apr  5 09:49:26 localhost kernel: [221721.356158]  sdb: sdb1
Apr  5 09:49:30 localhost kernel: [221725.041700] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Apr  5 09:49:30 localhost kernel: [221725.046233] sd 4:0:0:0: Attached scsi generic sg2 type 0
Apr  5 09:49:49 localhost kernel: [221744.322310] usb 5-2.4: USB disconnect, address 100
Apr  5 09:50:14 localhost kernel: [221768.540948] usb 5-2.4: new full speed USB device using ehci_hcd and address 101
Apr  5 09:50:14 localhost kernel: [221768.634268] usb 5-2.4: configuration #1 chosen from 1 choice
Apr  5 09:50:14 localhost kernel: [221768.634749] scsi5 : SCSI emulation for USB Mass Storage devices
Apr  5 09:50:19 localhost kernel: [221773.627563] scsi 5:0:0:0: Direct-Access     Generic  Audio Player     0100 PQ: 0 ANSI: 4
Apr  5 09:50:19 localhost kernel: [221773.651490] sd 5:0:0:0: [sdb] 484224 2048-byte hardware sectors (992 MB)
Apr  5 09:50:19 localhost kernel: [221773.655484] sd 5:0:0:0: [sdb] Write Protect is off
Apr  5 09:50:19 localhost kernel: [221773.659468] sd 5:0:0:0: [sdb] 484224 2048-byte hardware sectors (992 MB)
Apr  5 09:50:19 localhost kernel: [221773.663466] sd 5:0:0:0: [sdb] Write Protect is off
**Apr  5 09:50:19 localhost kernel: [221773.663496]  sdb: sdb1**
Apr  5 09:50:22 localhost kernel: [221776.535909] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Apr  5 09:50:22 localhost kernel: [221776.535970] sd 5:0:0:0: Attached scsi generic sg2 type 0
```

---

