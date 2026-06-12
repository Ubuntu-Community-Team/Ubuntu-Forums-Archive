---
title: "[SOLVED] Cant Find WD MyBook 2 Pro RAID Drive"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2008-02-05
I got a Western Digital MyBook II 1terabyte RAID drive which i am planning to use in my server running Ubuntu Gutsy.

I plugged it into my desktop (via firewire so creating the ext3 filesystem would be quicker) but now when i plug it into my server (Via USB 1.1) i cannot find it. It doesnt seem to show up in /dev and i cant think of anywhere else to look. I checked my kernel log to see if it was complaining but there were no obvious errors and the kernel does seem to find the disk:

```
Feb  5 20:58:57 penguin kernel: [   30.851784] usb-storage: device scan complete
Feb  5 20:58:57 penguin kernel: [   30.858778] scsi 2:0:0:0: Enclosure         WD       My Book Device   104a PQ: 0 ANSI: 4
Feb  5 20:58:57 penguin kernel: [   30.882754] scsi 2:0:0:1: Direct-Access     WD       My Book          104a PQ: 0 ANSI: 4
Feb  5 20:58:57 penguin kernel: [   30.883123] scsi 2:0:0:0: Attached scsi generic sg3 type 13
```

though i dont know what this means. Can anyone help?

---

### Post by bobbocanfly on 2008-02-05
Fixed this. Was just showing up the wrong number of partitions but managed to work it out by catting proc/paritions and reading the partition size.

---

