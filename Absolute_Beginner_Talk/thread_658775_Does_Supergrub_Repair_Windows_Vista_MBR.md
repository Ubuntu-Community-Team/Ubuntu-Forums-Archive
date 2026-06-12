---
title: "Does Supergrub Repair Windows Vista MBR?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by radlations on 2008-01-05
Im trying to uninstall the Ubuntu partition and have only Windows Vista.

First Im supose to repair the MBR.

I do not have the Windows Vista installation Disk. ALTHOUGH I just did a Recovery to Factory settings from my Recovery Partition. I now have a clean slate. Linux does not boot on startup. BUT I am still missing 40GB of space(40gb was the size of the Ubuntu partition)

**Did the recovery to factory settings repair the MBR?**

If not I am looking into the Super Grub method for repairing Windows MBR.

[B]But I don't know if Supergrub repairs Windows Vista's MBR.
[/B]

Help Please.

---

### Post by nitro_n2o on 2008-01-05
So, if you installed linux then windows this might help [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) the liveCD can do all the work

---

### Post by logos34 on 2008-01-05
> **radlations said:**
> If not I am looking into the Super Grub method for repairing Windows MBR.

[B]But I don't know if Supergrub repairs Windows Vista's MBR.
[/B]

According to [this post]("http://ubuntuforums.org/showpost.php?p=4003118&postcount=10") it does.

---

### Post by radlations on 2008-01-05
Thank you for your replies but it seems that recoverying your notebook to factory settings does in fact repair the MBR.

I just got popped my Ubuntu livecd in and ran Gparted, deleted the Ubuntu partition and gave it back to Windows.

Windows loaded fine after the restart.

---

