---
title: "Frequently hanging applications after update to Feisty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by bartaz on 2007-04-21
The problem I have with Feisty is exactly the same as already discussed in Feisty Development Forum ([Laptop hangs mercilessly after update to Feisty]("http://ubuntuforums.org/showthread.php?p=2467922") ), but now it's closed without solution.

Almost every application hangs from time to time. Even when I'm writing this post after few words firefox hanged for a few seconds. When I'm watching a move mplayer hangs few times per hour.

At first I thought it might be Beryl causing problems but I checked it and it's the same in metacity and in compiz. So it is not a problem with window manager I guess.
I even had system monitor opened to check if something strange happens when apps are hanging but there is nothing in there. No hi memory or cpu usage.

If anyone has a clue what can it be and how to fix it I'll be grateful.

---

### Post by morphious on 2007-04-22
Check your dmesg.

If you have something like this:

> [ 4535.380000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4535.380000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x1e data 0
[ 4535.380000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 4542.384000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 4565.400000] ata1: port failed to respond (30 secs, Status 0xd0)
[ 4565.400000] ata1: soft resetting port
[ 4565.808000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[ 4565.816000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[ 4565.816000] ata1.00: configured for UDMA/100
[ 4566.000000] ata1.01: configured for UDMA/33
[ 4566.000000] ata1: EH complete
[ 4566.008000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 4566.232000] sda: Write Protect is off
[ 4566.232000] sda: Mode Sense: 00 3a 00 00
[ 4566.236000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4566.236000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 4566.236000] sda: Write Protect is off
[ 4566.236000] sda: Mode Sense: 00 3a 00 00

It means, that you experience freezes because of your hard disk and bugs in kernel.
See related topic: [here]("http://ubuntuforums.org/showthread.php?t=408524").

---

### Post by bartaz on 2007-04-22
Yes.
That is my problem. So we need to wait till some fix or keep CD in a drive (this workaround works for me).

Thanks for your reply.

---

