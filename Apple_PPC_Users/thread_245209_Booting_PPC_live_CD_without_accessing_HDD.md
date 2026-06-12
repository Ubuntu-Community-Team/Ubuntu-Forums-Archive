---
title: "Booting PPC live CD without accessing HDD?"
date: 2006-08-27
forum: Apple PPC Users
---

### Post by rdemanow on 2006-08-27
I have a G3 iBook which has a partially corrupted hard drive.  It won't boot OS X (crashes on loading certain driver modules), but it *will* boot in single user mode, and I can look through the file system in read-only mode.

I'd like to salvage some data off of this drive.  OS X's single user mode won't recognize a USB or FireWire drive when plugged into it, and for some reason the "Target Drive" mode won't let me mount it on another Mac (keeps saying "invalid parameter" when I issue the command 'mount -t hfs -r /dev/disk1s10 /Volumes/iBook' -- which is a perfectly valid mount command.)

Anyway, I thought I'd try using Ubuntu to boot into a working OS, mount the external USB or FireWire drive, and copy the data over.

The problem is that the Live CD keeps trying to do something with the internal hard drive -- I'm guessing it's trying to run fsck on it? -- it keeps getting I/O errors and won't finish booting. ](*,) 

Is there a parameter that I can pass to yaboot at the boot: prompt to prevent the system from trying to access the internal hard drive until I'm ready to manually  mount it read-only?

Thanks,

RichD

---

