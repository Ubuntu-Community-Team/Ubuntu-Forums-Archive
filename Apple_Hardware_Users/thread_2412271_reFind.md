---
title: "reFind"
date: 2019-02-10
forum: Apple Hardware Users
---

### Post by j3984 on 2019-02-10
If you do a dual boot on a Mac and want Ubuntu to always load auto instead of OS....you can skip ReFind,yes? how would you do that?

---

### Post by &amp;KyT$0P# on 2019-02-10
Yes and you don't need to do anything.  Current versions of Ubuntu automatically put GRUB first in the bootorder.

---

### Post by j3984 on 2019-02-11
great
installing ReFind and dealing with SIP is a pain so that makes it easy. I want 18.04 in there. I have 8 gig ram so I will also skip SWAP partition.

---

### Post by j3984 on 2019-02-11
" Current versions of Ubuntu automatically put GRUB first in the bootorder"
are you sure of this?? for 18.04   mac air/ubuntu  dual boot

---

### Post by &amp;KyT$0P# on 2019-02-11
It does in my MacBook Pro.

If this is not the case for your Mac, please post the output from running this command in Terminal (from your installed Ubuntu 18.04) -
```
efibootmgr -v
```

Also what is the exact model number of your "mac air"?

---

