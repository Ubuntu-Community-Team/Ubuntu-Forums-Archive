---
title: "Error messages on every boot..?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-06-23
On every boot of Feisty 64-bit, with no usplash, one of the very first messages I see is a series of 4 or 5 lines beginning with "kinit:" and then an error message.  It flashes by so quickly that I can't exactly make out what it is, but it seems to be saying that it's trying to resume from a disk, and that this fails, and it's trying a normal boot.  It slows down my boot, but still goes by too quickly to write it all down.

The closest match to it I can find in my log files is this:

```

Jun 23 15:11:53 ub64 kernel: [   35.024129] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 23 15:11:53 ub64 kernel: [   35.024131]  sdd: sdd1
Jun 23 15:11:53 ub64 kernel: [   35.047098] sd 3:0:0:0: Attached scsi disk sdd
Jun 23 15:11:53 ub64 kernel: [   35.050824] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 23 15:11:53 ub64 kernel: [   35.050844] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jun 23 15:11:53 ub64 kernel: [   35.050863] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jun 23 15:11:53 ub64 kernel: [   35.050882] sd 3:0:0:0: Attached scsi generic sg3 type 0
Jun 23 15:11:53 ub64 kernel: [   35.215685] Attempting manual resume
Jun 23 15:11:53 ub64 kernel: [   35.215689] swsusp: Resume From Partition 8:21
Jun 23 15:11:53 ub64 kernel: [   35.215691] PM: Checking swsusp image.
Jun 23 15:11:53 ub64 kernel: [   35.215815] PM: Resume from disk failed.
Jun 23 15:11:53 ub64 kernel: [   35.239535] kjournald starting.  Commit interval 5 seconds
Jun 23 15:11:53 ub64 kernel: [   35.239545] EXT3-fs: mounted filesystem with ordered data mode.

```

A newbie wild guess: it's seeing if it was in some kind of suspended or sleep mode, trying to resume the session, discovering there's nothing to resume, and then going about booting normally?

Since I don't use suspect or hibernate modes, is there any way to keep it from doing this, assuming of course that my guess is correct?

Or, do I have a more serious problem of some kind with this install?

Thanks,
Bob

---

### Post by Jimmyfj on 2007-06-23
Have you tried the "Start Ubntu in safe graphics mode" ?

If you have, then I suggest you try out the alternate install cd

---

### Post by RTrev on 2007-06-23
> **Jimmyfj said:**
> Have you tried the "Start Ubntu in safe graphics mode" ?

If you have, then I suggest you try out the alternate install cd

Well, this is an install from the "mini" CD, because I wanted to get rid of all the bloat.  Perhaps it isn't clear from my question, but my system boots up and runs fine, so it isn't a matter of having to go in and fix something so I can boot.  I'm just wondering if there is something wrong with my install.  It seems to me that even when I had the full blown version of Ubuntu installed, I would find similar messages in my logs.  Never knew what they were.  It wasn't until I did the minimal install and got rid of the uspash that I began seeing it happening live.

Maybe I'm missing your point..?

BTW, you aren't the same Jimmy as over on the grc newsgroups are you?  :-)

Thanks,
Bob

---

### Post by Crafty Kisses on 2007-06-23
> **RTrev said:**
> On every boot of Feisty 64-bit, with no usplash, one of the very first messages I see is a series of 4 or 5 lines beginning with "kinit:" and then an error message.  It flashes by so quickly that I can't exactly make out what it is, but it seems to be saying that it's trying to resume from a disk, and that this fails, and it's trying a normal boot.  It slows down my boot, but still goes by too quickly to write it all down.

The closest match to it I can find in my log files is this:

```

Jun 23 15:11:53 ub64 kernel: [   35.024129] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 23 15:11:53 ub64 kernel: [   35.024131]  sdd: sdd1
Jun 23 15:11:53 ub64 kernel: [   35.047098] sd 3:0:0:0: Attached scsi disk sdd
Jun 23 15:11:53 ub64 kernel: [   35.050824] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 23 15:11:53 ub64 kernel: [   35.050844] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jun 23 15:11:53 ub64 kernel: [   35.050863] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jun 23 15:11:53 ub64 kernel: [   35.050882] sd 3:0:0:0: Attached scsi generic sg3 type 0
Jun 23 15:11:53 ub64 kernel: [   35.215685] Attempting manual resume
Jun 23 15:11:53 ub64 kernel: [   35.215689] swsusp: Resume From Partition 8:21
Jun 23 15:11:53 ub64 kernel: [   35.215691] PM: Checking swsusp image.
Jun 23 15:11:53 ub64 kernel: [   35.215815] PM: Resume from disk failed.
Jun 23 15:11:53 ub64 kernel: [   35.239535] kjournald starting.  Commit interval 5 seconds
Jun 23 15:11:53 ub64 kernel: [   35.239545] EXT3-fs: mounted filesystem with ordered data mode.

```

A newbie wild guess: it's seeing if it was in some kind of suspended or sleep mode, trying to resume the session, discovering there's nothing to resume, and then going about booting normally?

Since I don't use suspect or hibernate modes, is there any way to keep it from doing this, assuming of course that my guess is correct?

Or, do I have a more serious problem of some kind with this install?

Thanks,
Bob
Hmmm, try booting in verbose mode, and see where the error actually occurs.

---

### Post by RTrev on 2007-06-23
> **Codename said:**
> Hmmm, try booting in verbose mode, and see where the error actually occurs.

Well, I'm having trouble (noob-style).  I edited /boot/grub/menu.lst and removed the "quiet", and it did indeed boot up very verbosely but at a speed Spock couldn't have read.  :)

The log of the boot looks just the same as the last time.  Not sure how to capture the error messages...??

Thanks,
Bob

p.s.  Looked at the actual "boot" log, instead of the kernel log, but it says "Nothing has been logged yet."  Maybe there's some way to turn that on?

---

