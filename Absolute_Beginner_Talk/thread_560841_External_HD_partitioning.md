---
title: "External HD partitioning"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-09-26
hey guys,

Ive checked out some other posts but here is the rundown. I have an external 200 GB drive in NTFS (and no I dont want to use Nt-fs for mounting lol). What can I use either than gparted to get a 20 GB partition for Linux and keep the rest NTFS? (and is FAT 32 a good idea for this partition?) Im gonna be installing grub on this 20 GB partition as well 


thanks in advance

---

### Post by mikewhatever on 2007-09-26
What's wrong with Gparted? You can use Qparted, a similar kind of program. FAT32 is not bad for storage, but isn't too good for numerous reads/writes. Linux has its own file system, ext3.

---

### Post by JasonBourneLinux on 2007-09-26
well, Ive always gotten error messages with Gparted (even if the drives were properly unmounted and such). I heard there are size limitations with FAT32 and windows.

Perhaps i can allocate 20 GB for FAT32 then rest NTFS and get NTFS mounter onto linux partition and go from there

---

