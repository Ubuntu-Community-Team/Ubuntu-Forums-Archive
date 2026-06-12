---
title: "Can't created Extended partition w/ gparted"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by zmike1 on 2007-05-05
I'm trying to install ubuntu on a Dell laptop.  Well, first, I'm trying to set up partitions so I can still use the "media direct" button and preserve the restore partition that already existed. I already resized the XP partition so that now gparted shows that I have a FAT16, NTFS, unallocated, and FAT32 partitions.

The desire: I'm trying to make the unallocated space into an "extended" partition so I can use it for ubuntu and swap and maybe another FAT 32 for sharing files with XP.

The problem: when I run gparted from a live CD, it doesn't allow the option of making the unallocated space into a new, extended partition.  It only allows a primary partition.  The other options are greyed-out so they are not selectable.  This is such the wrongness.  

Is this a limitation in gparted?
Is there something I'm missing (more likely)?

---

### Post by Bachstelze on 2007-05-05
Do you have an extended partition already ? There can be only one of them on a given disk.

---

### Post by zmike1 on 2007-05-05
Yes.  the last FAT32 partiton is Extended.  I knew about the 4 primary limit but never heard of the 1 Extended limit..
Thank you.  
It seems, however, that I'll be unable to save the last partition (which I think contains the Restore Image) but I'll work on it.
Thanks again.
-Z

---

