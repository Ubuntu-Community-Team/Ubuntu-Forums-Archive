---
title: "problem booting ubuntu"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by sleaze on 2008-03-18
i hav windows xp installed..now i installed ubuntu 7.04 and when i restart the system after removing the ubuntu cd,I am not getting the option of selecting the OS to boot and by default xp is booted...can anyone provide me a solution..??

---

### Post by logos34 on 2008-03-18
Boot from the live cd and run post the output from this terminal command:

sudo fdisk -l

If you have more than one hard disk, sata or pata/ide? Could be that grub installed on the other disk's mbr.  Or menu.lst is configured to default to xp boot.  Or grub didn't install at all.

You can try[ reinstalling grub]("http://ubuntuforums.org/showthread.php?t=224351").

---

