---
title: "Ubuntu 10.10 G4 iLamp Maverick Meerkat"
date: 2010-10-25
forum: Apple Hardware Users
---

### Post by Beeblejj on 2010-10-25
Install and boots fine, however it hangs on the splash screen.
**Stalls at:**
> fb: conflicting fb hw usage nouveaufb vs 0Ffb NVDA,NVMac - removing generic driver[B]
The whole sequence looks like:[/B]
> fsck from util-linux-ng 2.17.2
/dev/hda3: clean, 109720/4767744 file, 817289/19063552 blocks
pidof[470]: can't read sid from 466/stat

[Time Code] hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
[Time Code] hda: task_no_data_intr: error=0x04 { DriveStatusError }
[Time Code] hda: possibly failed opcode: 0xef
* Starting AppArmor profiles
[Time Code] fb: conflicting fb hw usage nouveaufb vs 0Ffb NVDA,NVMac - removing generic driver

---

### Post by Beeblejj on 2010-10-26
Tried reinstalling and changing from ext4 to ext3. Same problem.

---

### Post by conal on 2010-10-26
> fb: conflicting fb hw usage nouveaufb vs 0Ffb NVDA,NVMac - removing generic driver 


Hi, just a suggestion (somebody correct me if this is not relevant): I have had many problems with the 'Nouvaeu' driver on my G4 iMac with several distros. Maybe you need to switch to 'nv' (the older video driver for these cards):

I have just done this with MintPPC 9 so it might work with Maverick Meercat as they are both based on Debian:

(If you can) get a command prompt by pressing Ctrl+Alt+F1, and log in. 

I used this guide to generate an xorg.conf file:

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html) 

Except before restarting GDM I opened the xorg.conf file using Nano (sudo nano /etc/X11/xorg.conf) and changed "nouveau" to "nv"

Then saved the changed file and restarted. 

Thanks

Conal

---

### Post by Beeblejj on 2010-10-26
> **conal said:**
> (If you can) get a command prompt by pressing Ctrl+Alt+F1, and log in. 

Thank you very much for the idea, however I can't even boot into anything past the splash screen.

---

