---
title: "Still seeking help, please"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by kubobbu on 2007-04-08
Still seeking help with my problem. Have loaded Xubuntu on an old Thinkpad 600 with 192MB of ram and a 40GB hard drive.  After loading, I attempted to reboot from hard drive, and got a Grub 18 error.  Research shows this means BIOS can't find boot info.

Yabadabadont was kind enough to suggest I create boot partition early on disk and make it bootable, but did not provide detail information. Can I repartition existing install, or do I have to manually partition as part of a new install process. And exactly what partitions do I need to make, and will the install then know automatically where to put needed data, even if it didn't in the first place?

Current partitions as installed are:

      /dev/hda1       ext3    36.82GB     Flag  boot
     /dev/hda2       extended   458.97MB
    /dev/hda5       linux-swap  454.94MB

Been playing with this all weekend... finally got successful install, only to have this problem. Would really appreciate help with this final step.

Thanks!!

---

### Post by overdrank on 2007-04-08
> **kubobbu said:**
> Still seeking help with my problem. Have loaded Xubuntu on an old Thinkpad 600 with 192MB of ram and a 40GB hard drive.  After loading, I attempted to reboot from hard drive, and got a Grub 18 error.  Research shows this means BIOS can't find boot info.

Yabadabadont was kind enough to suggest I create boot partition early on disk and make it bootable, but did not provide detail information. Can I repartition existing install, or do I have to manually partition as part of a new install process. And exactly what partitions do I need to make, and will the install then know automatically where to put needed data, even if it didn't in the first place?

Current partitions as installed are:

      /dev/hda1       ext3    36.82GB     Flag  boot
     /dev/hda2       extended   458.97MB
    /dev/hda5       linux-swap  454.94MB

Been playing with this all weekend... finally got successful install, only to have this problem. Would really appreciate help with this final step.

Thanks!!

Hi you might try this thread and reinstall grub.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Hope this helps good luck and welcome!:popcorn:

---

### Post by trent dillman on 2007-04-08
...

---

### Post by kubobbu on 2007-04-08
Thanks, Paul.  I tried the process outlined in the post you referenced, but when I rebooted the computer, Grub Error 18 again.  I guess the problem is not defective grub, but a partition/location problem.

I guess I will have to reinstall, but would appreciate it if someone could give me the correct partitioning info I will need to insure that everything gets loaded where the bios can find what it needs to boot.

Thanks, and Happy Holiday to all.

---

### Post by trent dillman on 2007-04-08
...

---

