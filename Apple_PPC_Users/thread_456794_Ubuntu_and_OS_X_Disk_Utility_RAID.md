---
title: "Ubuntu and OS X Disk Utility RAID"
date: 2007-05-28
forum: Apple PPC Users
---

### Post by EuroCity on 2007-05-28
I would like to mount a striped RAID array, formatted with OS X 10.4.9's Disk Utility, in Ubuntu 7.04 PPC: I tried this some time ago, but the two disks of the RAID appeared as separate volumes in Nautilus and in GParted (or QtParted).

Is there a way to make an */etc/fstab* entry for an Apple software RAID volume in Ubuntu?

Linux tools, such as *dmraid* or others, if installed, don't seem to recognise an Apple RAID: or am I wrong?

For example, an ordinary HFS+ Journaled volume would be something like this:

```
/dev/hda3 /media/macosx hfsplus defaults 0 0
```

... to mount it read-only: but what about a RAID formatted with Apple's Disk Utility?

Has someone tried that?

(Of course, all this is also because I want to use the striped RAID primarily in Mac OS X, as a */Users* data volume: so it wouldn't really be too good to format it as a RAID in Ubuntu, probably.)

---

