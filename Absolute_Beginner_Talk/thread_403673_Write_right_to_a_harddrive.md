---
title: "Write right to a harddrive"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by logicus on 2007-04-07
Hi there..
yes, it's me again ;-)

I've got this nice USB harddrive that I've connected to my Ubuntu. however when I try to save files on it from linux it tells me that:You cannot drop items in a directory in which you do not have write permission.

Can you please tell me what to do ?
Thank You very much.

---

### Post by mac.ryan on 2007-04-07
What filesystem have you formatted your HD in? (NTFS, EXT3, FAT32...?)

If it is a NTFS, then the default ubuntu setting is "write only". If it is EXT3, it must be a wrong permission setting.

There are workarounds for both... just tell us what situation are you in! :)

---

### Post by logicus on 2007-04-07
Hi again

The filesystem is NTFS..

Made with loving hand in windows XP.. :)

---

### Post by yabbadabbadont on 2007-04-07
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

You have to use additional software if you wish to have write support for NTFS.  That guide explains how.

---

### Post by logicus on 2007-04-07
It worked..
thanks, man

:KS

---

