---
title: "Changing tripleboot to dualboot"
date: 2017-07-25
forum: Apple Hardware Users
---

### Post by Donnut on 2017-07-25
Hi there. So I have a laptop that's triplebooted OSX, Ubuntu, and Windows. OSX is first on the partition table, (after EFI), than Windows, then Swap, then Ubuntu. Is there anyway to wipe Windows and put Ubuntu third on the table leaving the Ubuntu installation intact?

---

### Post by oldfred on 2017-07-25
Moved to the Apple hardware users sub-forum.

Do not know Mac, but post these, not sure even with Mac what you get with these:
sudo parted -l
sudo efibootmgr -v

---

