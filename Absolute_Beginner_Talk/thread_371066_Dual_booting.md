---
title: "Dual booting"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by sirlord on 2007-02-26
Have just installed ubuntu 6.10 on a drive with xppro.  Grub correctly identifies both systems, but if xppro is selected, windows reports it cannot start successfully.  Booting in safe mode fails as the computer simply reboots from scratch which takes me back to Grub.  Is there a way to fix the dual boot option?  I am reluctant to try this within windows as I would expect it to overwrite, or at least not recognize, the linux partition.

---

### Post by netkid91 on 2007-02-26
You more than likely fried your windows partition.  Did you resize the NTFS partition during the install?

---

### Post by Sbarton on 2007-02-26
If you have your Win CD you may be able to 'fix/mbr' through the recovery console.
regards

---

### Post by netkid91 on 2007-02-26
It isn't and MBR error.  It is NTLDR saying that it cannot load the system (NTLDR is located on the actual Windows partition, all the Windows MBR is transfer execution to NTLDR).

---

### Post by Patrick K on 2007-02-26
I know nothing about XP but maybe the partition needs to be set active/bootable. Take a look with GParted. IIRC, you can set it active (Boot) with GParted, if it isn't already.

---

