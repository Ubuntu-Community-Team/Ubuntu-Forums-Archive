---
title: "Read a Mac Hard Drive"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by jacyk on 2006-09-19
I am running Ubuntu on extra pc that I had. I have an old Mac Performa that has some data on it that I would like to be able to transfer to a CD. Seeing how the mac doesn't have a cd-burner and the floppy is shot, if I hook up the hard drive out of the mac to the pc, will I be able to read the hard drive so that I can make the data cd? I can't afford to lose the information so I wanted to ask before I just hooked it up and see what happens.

Thanks

---

### Post by kidders on 2006-09-20
Hi there,

Well you won't do any damage, if that's what you're worried about :-) In general, the Linux kernel is capable of reading Apple partition maps ... I'm assuming Ubuntu can too, and that the right modules will autoload for you.

The one thing you need to be aware of is that the partition numbering scheme might seem a bit alien to you, if you're used to Bill Gates' partition model. There'll probably be a few apparently redundant /dev entries that have no filesystem on the other end ... but that's normal.

If you're feeling a bit unsteady about the whole thing, mount your HFS (I'm assuming that's what's there!) partitions read-only. Incidentally, Linux will moan about journalised HFS and refuse to let your write to it :-(

---

### Post by jacyk on 2006-09-20
Okay. I have yet to have to deal with a scsi drive in linux. I know that an IDE is usally hda1, hda2 and so forth. Am I right in thinking that the scsi from the mac will be sda1?

Thanks

---

### Post by kidders on 2006-09-20
I imagine so, yes. In any case, your **dmesg** will tell you what's going on. For instance, here's a wee extract from mine...

```
[17179578.152000] SCSI device sda: 390719855 512-byte hdwr sectors (200049 MB)
[17179578.152000] SCSI device sda: drive cache: write back
[17179578.156000] SCSI device sda: 390719855 512-byte hdwr sectors (200049 MB)
[17179578.156000] SCSI device sda: drive cache: write back
[17179578.156000]  sda: sda1 sda2 sda3
[17179578.184000] sd 3:0:0:0: Attached scsi disk sda
[17179578.196000] SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
[17179578.196000] SCSI device sdb: drive cache: write back
[17179578.200000] SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
[17179578.200000] SCSI device sdb: drive cache: write back
[17179578.200000]  sdb: sdb1
[17179578.216000] sd 4:0:0:0: Attached scsi disk sdb

```

Assuming I'd never used either of those disks before, it's easily enough information to get me started. A little further down, I see my IDE stuff ...

```

[17179578.444000] Probing IDE interface ide0...
[17179579.588000] hdb: AOPEN COM5232/AAH PRO, ATAPI CD/DVD-ROM drive
[17179579.644000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

```

So, once your drive is plugged in, and your all freshly booted, anything unfamiliar-looking is what you're after.

If you wanted, you could use **diff** to run a comparison between two **dmesg** sets ...

[LIST=1]
[*]Without your Mac disk, do a clean boot and type **dmesg >~/old_dmesg**
[*]With your Mac disk, type **dmesg >~/new_dmesg**
[*]Take a look at the output of **diff ~/old_dmesg ~/new_dmesg**
[/LIST]

In theory, anything that's the same in both versions would be hidden.

---

### Post by jacyk on 2006-09-26
Well I finally got around to giving it a shot. Worked with no problems. It did come up as sda1 in case anyone else has a similar issue. Thanks:)  for the help.

---

