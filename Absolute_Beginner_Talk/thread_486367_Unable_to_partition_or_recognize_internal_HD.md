---
title: "Unable to partition or recognize internal HD"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by PaperChase on 2007-06-27
Hi Ubuntu Community,

I'll try to explain what happened as best as I can. Hopefully someone knows what the problem is or how to fix it. I did an extensive search of these forums and Google and found nothing that was quite the same case as mine, but here goes anyway...

I decided yesterday to install Ubuntu off a live CD. The live CD booted up without a hitch, and everything was going great until I began to partition my internal HD (using guided, not manual). Something went wrong and I got a "failed to partition hard drive" message. I can't remember the details of the message, but it happened around 15%. So I tried again, and the same thing happened, only this time it was around 5%. After some searching through help menus and forums, I went into Gparted and found that my hard drive was not being recognized by Ubuntu. I pressed "refresh devices" a few times and still nothing. So I rebooted, and in the splash screen I decided to scan the disk to see what was wrong. Since then, every time I boot Ubuntu off the CD, I get a message that was the equivalent of about 10 minutes worth of white letters saying roughly the equivalent of this dmesg:


 > hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=64, high=0, low=64, sector=64
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 64
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 8
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=56
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 56
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=64, high=0, low=64, sector=64
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 64
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=56
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 56
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=64, high=0, low=64, sector=64
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 64
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 8
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=56
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 56
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=64, high=0, low=64, sector=64
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 64
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=64, high=0, low=64, sector=64
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 64
printk: 2 messages suppressed.
Buffer I/O error on device hda, logical block 8
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=64, high=0, low=64, sector=64
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 64
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=64, high=0, low=64, sector=64
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 64
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 8
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=64, high=0, low=64, sector=64
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 64
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=64, high=0, low=64, sector=64
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 64
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=1, high=0, low=1, sector=1
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 1
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=2, high=0, low=2, sector=2
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 2
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=3, high=0, low=3, sector=3
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 3
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=4, high=0, low=4, sector=4
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 4
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 4
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=5, high=0, low=5, sector=5
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 5
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=6, high=0, low=6, sector=6
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 6
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=7, high=0, low=7, sector=7
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 7
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=1, high=0, low=1, sector=1
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 1
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=2, high=0, low=2, sector=2
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 2
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=3, high=0, low=3, sector=3
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 3
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=4, high=0, low=4, sector=4
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 4
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 4
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=5, high=0, low=5, sector=5
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 5
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=6, high=0, low=6, sector=6
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 6
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=7, high=0, low=7, sector=7
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 7
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
EFS: cannot read volume header
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=1, high=0, low=1, sector=1
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 1
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=2, high=0, low=2, sector=2
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 2
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=3, high=0, low=3, sector=3
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 3
printk: 2 messages suppressed.
Buffer I/O error on device hda, logical block 3
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=4, high=0, low=4, sector=4
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 4
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=5, high=0, low=5, sector=5
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 5
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=6, high=0, low=6, sector=6
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 6
printk: 2 messages suppressed.
Buffer I/O error on device hda, logical block 6
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=7, high=0, low=7, sector=7
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 7
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=1, high=0, low=1, sector=1
ide: failed opcode was: unknown
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=1, high=0, low=1, sector=1
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 1
printk: 2 messages suppressed.
Buffer I/O error on device hda, logical block 1
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=2, high=0, low=2, sector=2
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 2
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=3, high=0, low=3, sector=3
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 3
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=4, high=0, low=4, sector=4
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 4
printk: 2 messages suppressed.
Buffer I/O error on device hda, logical block 4
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=5, high=0, low=5, sector=5
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 5
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=6, high=0, low=6, sector=6
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 6
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=7, high=0, low=7, sector=7
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 7
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=1, high=0, low=1, sector=1
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 1
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=2, high=0, low=2, sector=2
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 2
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=3, high=0, low=3, sector=3
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 3
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=4, high=0, low=4, sector=4
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 4
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 4
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=5, high=0, low=5, sector=5
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 5
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=6, high=0, low=6, sector=6
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 6
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=7, high=0, low=7, sector=7
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 7
printk: 2 messages suppressed.
Buffer I/O error on device hda, logical block 7
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=1, high=0, low=1, sector=1
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 1
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=2, high=0, low=2, sector=2
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 2
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=3, high=0, low=3, sector=3
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 3
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 3
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=4, high=0, low=4, sector=4
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 4
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=5, high=0, low=5, sector=5
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 5
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=6, high=0, low=6, sector=6
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 6
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=7, high=0, low=7, sector=7
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 7
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 7
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=56
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 56
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=57
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 57
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=58
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 58
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=59
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 59
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 59
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=60
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 60
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=61
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 61
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=62
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 62
printk: 2 messages suppressed.
Buffer I/O error on device hda, logical block 62
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=63
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 63
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=64, high=0, low=64, sector=64
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 64
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=66, high=0, low=66, sector=65
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 65
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=66, high=0, low=66, sector=66
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 66
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 66
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=56
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 56
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=57
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 57
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=58
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 58
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=59
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 59
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 59
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=60
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 60
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=61
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 61
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=62
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 62
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=63
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 63
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 63
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=56
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 56
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=57
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 57
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=58
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 58
printk: 2 messages suppressed.
Buffer I/O error on device hda, logical block 58
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=59
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 59
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=60
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 60
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=61
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 61
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=62
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 62
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 62
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=63, high=0, low=63, sector=63
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 63
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=1, high=0, low=1, sector=1
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 1
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=2, high=0, low=2, sector=2
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 2
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 2
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=3, high=0, low=3, sector=3
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 3
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=4, high=0, low=4, sector=4
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 4
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=5, high=0, low=5, sector=5
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 5
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=6, high=0, low=6, sector=6
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 6
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 6
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=7, high=0, low=7, sector=7
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 7
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=1, high=0, low=1, sector=1
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 1
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=2, high=0, low=2, sector=2
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 2
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 2
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=3, high=0, low=3, sector=3
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 3
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=4, high=0, low=4, sector=4
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 4
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=5, high=0, low=5, sector=5
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 5
printk: 2 messages suppressed.
Buffer I/O error on device hda, logical block 5
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=6, high=0, low=6, sector=6
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 6
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=7, high=0, low=7, sector=7
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 7
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=1, high=0, low=1, sector=1
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 1
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 1
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=2, high=0, low=2, sector=2
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 2
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=3, high=0, low=3, sector=3
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 3
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=4, high=0, low=4, sector=4
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 4
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=5, high=0, low=5, sector=5
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 5
printk: 3 messages suppressed.
Buffer I/O error on device hda, logical block 5
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=6, high=0, low=6, sector=6
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 6
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=7, high=0, low=7, sector=7
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 7
hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=0, high=0, low=0, sector=0
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 0
EFS: cannot read volume header
end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
printk: 2 messages suppressed.
Buffer I/O error on device fd0, logical block 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0

Anyway, I booted Knoppix and checked it out, and Knoppix can see my hard drive, but cannot mount it (I'm not an expert on this, but Knoppix says that it cannot determine the filesystem type, and none was specified). However, Ubuntu still cannot see my hard drive in any programs, including Gparted and the partitioner that runs during the installer. I can't boot off my HD either.

I'm not sure if there are any other important details I left out, but it would be nice to see what everyone thinks. Any help anyone can give is appreciated, thanks for your time!

---

### Post by rickycodie on 2007-06-27
first off what kind of hard drive do you have?

---

### Post by PaperChase on 2007-06-28
I have a 160 gig Maxtor 6Y160P0.

---

### Post by PaperChase on 2007-06-29
Bump... anyone?

---

