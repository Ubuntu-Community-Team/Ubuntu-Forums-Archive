---
title: "Find my Tape Drive on Edgy?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by neocookie on 2007-01-29
I've been tasked with installing a dev server with backups, and have been provisioned a box with a tape drive.

The drive is powered up, and seems to "scan" when I insert a tape. But from that point I'm a little lost.

I've checked /dev, and all I seem to have is a device called /dev/sg0. I've checked proc, and have /proc/scsi.

Is there a way I can find out "where" it is on my system, and get it running?

---

### Post by neocookie on 2007-01-30
Don't worry, found it. Did some bios tweaks, reset the SCSI card, etc. Seems to have appeared at /dev/st0.

---

