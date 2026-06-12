---
title: "Attach USB Memory Card Reader After Booting"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by TheDoulos on 2007-05-02
Running Kubuntu Feisty...

If I have my USB 10-in-1 memory card reader attached to my system *before* I boot, everything works great (put in a memory card, device automounts, kde puts up a window asking me what I want to do, life is good).

If I plug my card reader into the same USB port *after* Feisty boots, I have different results.  Inserting a memory card does not cause an automount to occur.  I'd go ahead and mount it manually if I knew it was really detected at all.  Is it really out there on a /dev/sd[something]?  Is there some USB autodetecting daemon that I should re-start after I connect the card reader to the USB port?

(BTW, same results w/ Edgy)

---

### Post by ubnewbie2 on 2007-05-02
try the command 

dmesg

after you insert the card.  The last few messages will about the card (if it is being seen).  For example, mine reports the card like this

[ 9885.714282] SCSI device sdf: 2012160 512-byte hdwr sectors (1030 MB)
[ 9885.716401] sdf: Write Protect is off
[ 9885.716405] sdf: Mode Sense: 03 00 00 00
[ 9885.716408] sdf: assuming drive cache: write through
[ 9885.720146] SCSI device sdf: 2012160 512-byte hdwr sectors (1030 MB)
[ 9885.722277] sdf: Write Protect is off
[ 9885.722283] sdf: Mode Sense: 03 00 00 00
[ 9885.722286] sdf: assuming drive cache: write through
[ 9885.722538]  sdf: sdf1

so you can

sudo mount /dev/sdf1 /<somewhere>

and yes, I have a card that it won't recognise, like you, and others that it will, although I haven't tried booting with the reader plugged in.

---

### Post by TheDoulos on 2007-05-02
Attaching the 4-slot card reader yields the following dmesg

```

[ 3738.458184] usb 6-4: new high speed USB device using ehci_hcd and address 3
[ 3738.607543] usb 6-4: configuration #1 chosen from 1 choice
[ 3738.610113] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3738.612776] usb-storage: device found at 3
[ 3738.612785] usb-storage: waiting for device to settle before scanning
[ 3743.606708] usb-storage: device scan complete
[ 3743.611346] scsi 4:0:0:0: Direct-Access     GENERIC  USB Storage-CFC  I16B PQ: 0 ANSI: 0 CCS
[ 3743.615716] scsi 4:0:0:1: Direct-Access     GENERIC  USB Storage-MSC  I16B PQ: 0 ANSI: 0 CCS
[ 3743.620086] scsi 4:0:0:2: Direct-Access     GENERIC  USB Storage-SMC  I16B PQ: 0 ANSI: 0 CCS
[ 3743.624457] scsi 4:0:0:3: Direct-Access     GENERIC  USB Storage-SDC  I16B PQ: 0 ANSI: 0 CCS
[ 3743.628251] sd 4:0:0:0: Attached scsi removable disk sdf
[ 3743.628701] sd 4:0:0:0: Attached scsi generic sg7 type 0
[ 3743.631644] sd 4:0:0:1: Attached scsi removable disk sdg
[ 3743.632104] sd 4:0:0:1: Attached scsi generic sg8 type 0
[ 3743.635152] sd 4:0:0:2: Attached scsi removable disk sdh
[ 3743.635640] sd 4:0:0:2: Attached scsi generic sg9 type 0
[ 3743.638805] sd 4:0:0:3: Attached scsi removable disk sdi
[ 3743.639311] sd 4:0:0:3: Attached scsi generic sg10 type 0

```

Even though /dev/sd[f,g,h,i] and /dev/sg[7,8,9,10] are created, and even though the LED lights up when I insert a memory card into one of the slots, and even though I created a new mount point (/media/SmartMedia0), I can't get the card to mount:

```

# mount /dev/sdh /media/SmartMedia0
mount: No medium found
# mount /dev/sg9 /media/SmartMedia0
mount: /dev/sg9 is not a block device

```

(yes, I tried sdf, sdg, sdi, sg7, sg8, and sg10)

---

### Post by ubnewbie2 on 2007-05-02
try doing a dmesg just after you insert the card, and see if messages similar to the ones I posted, appear.

---

### Post by TheDoulos on 2007-05-03
The example above *is* after the memory card is inserted.

There's a bit of activity when the card reader is attached, and dmesg shows the additional data listed above.  There's no additional dmesg information after the memory card is inserted.

I tried having a memory card already in the reader when it's attached, but that didn't help either.

---

### Post by ubnewbie2 on 2007-05-03
I don't think it's seeing the card at all. Have you (can you) try different cards and different readers?

---

### Post by TheDoulos on 2007-05-03
It seems that one of the slots on the card reader I was using was acting strangely.  I've got two card readers and plenty of memory cards, but I was primarily using an old Smart Media card (because I didn't care if the data on it got scrogged) and a small card reader that I move around a lot.

What's odd is that if I have that card reader attached when the machine boots, plugging in memory cards (even the Smart Media card) results in a proper auto mount and prompting.  If I plug that card reader in after boot time, the Smart Reader slot doesn't auto mount, but the other slots do (when I insert a memory card).

I have another card reader, and plugging it in after boot time yields proper behavior even with its Smart Media slot.

Oh well...I'm declaring it to be a non-problem.

Thanks for your feedback.

---

