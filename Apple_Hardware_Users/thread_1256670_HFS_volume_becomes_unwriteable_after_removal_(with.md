---
title: "HFS volume becomes unwriteable after removal (without unmounting)"
date: 2009-09-02
forum: Apple Hardware Users
---

### Post by gamgee911 on 2009-09-02
I have a HFS+ volume plugged in via usb.  It's not journaled so I can read/write to it and all's well.  However, if I unplug the drive w/o unmounting it or if the computer freezes and must be rebooted, the volume becomes unwriteable.  The only method I've been able to fix it with is plugging it into a mac and running diskutil disableJournal again and it fixes the problem - but is there an easier way just to do it in linux?

Sorry if this is technically wrong category, I figure most HFS questions come up in Apple however so you guys would be the experts :P  Thanks.

---

