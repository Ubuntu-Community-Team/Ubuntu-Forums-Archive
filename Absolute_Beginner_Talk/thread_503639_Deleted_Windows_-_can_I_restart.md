---
title: "Deleted Windows - can I restart?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by mikeb on 2007-07-18
This morning I reformatted my Windows partition and now use it for storing data in Ubuntu. My harddrive was partitioned:

/dev/hda1 -Windows (now contains only data files)
/dev/hda2 - older version of Ubuntu
/dev/hda4 - current Ubuntu

If I restart the computer, what will happen? Since /dev/hda1 contains no OS will Grub from the old version or the new version of Ubuntu automatically load? Is there anything I need to change or should it work as it is now?

---

### Post by Malta paul on 2007-07-18
Hi, Grub should be on the 'Master Boot Record' on your HD and your system should boot normal, I hope :wink:

---

### Post by MattDTownsend on 2007-07-18
If Grub isn't in the MBR, you can reinstall it with a live CD.  No worries.

---

### Post by mikeb on 2007-07-18
Many thanks for the replies. If it doesn't work, is there a procedure for how to reinstall Grub in the MBR? Thanks.

---

### Post by FunkyJack on 2007-07-18
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by mikeb on 2007-07-18
> **FunkyJack said:**
> [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Many thanks for your kind help!

---

