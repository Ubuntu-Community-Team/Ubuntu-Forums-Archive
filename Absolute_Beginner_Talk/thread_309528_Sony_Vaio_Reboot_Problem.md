---
title: "Sony Vaio Reboot Problem"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by ftabor on 2006-11-29
I have a Sony Vaio with dual-boot WinXP home and Breezy.  When I try to restart the computer from Breezy, All goes well till the last few steps of the shut down.

*Deactivating Swap
umount:tmpfs busy remounted read-only
*Unmount Local File System
umount: tmpfs busy emounted read-only
*Shutting down LVM Volume Groups
*Rebooting
[4295939.122000] restart System

Then it just sits there.  No disk activity, Nothing.  I let it sit for an hour before finally forcing power off.  The system restarts fine from Windows, and while it gives the same errors on unmounting, it will shut down fine on it's own from Breezy.

I haven't been able to find any posts with similar problems.  Thanks for any help I can get.

---

### Post by ReaderRat on 2006-11-29
Is it a laptop? If so, what model?

---

### Post by ftabor on 2006-11-29
Yes, it's a laptop.  VGN-FS760 is the model.

---

### Post by ReaderRat on 2006-11-29
I checked with the laptop testing site, but no helpful info found....sorry.

---

### Post by ftabor on 2006-12-01
I have corrected my own problems by upgrading to Dapper.  All seems well now.

---

