---
title: "Grub Error 18 Help"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by kubobbu on 2007-04-07
Thanks to those who helped with previous question.  Finally got Xubuntu to load on my old laptop... IBM Thinkpad 600 with 192MB of ram only to reboot without the CD and get a Grub 18 error.

Some research shows that this indicates that the boot sector is beyond the BIOS ability to find it. Since this machine has only limited BIOS access, I need to move the data on the hard drive to make it accessable.

Current partitions are:   /dev/hda1   ext3   36.2 GB     Flag "Boot"
                                           /dev/hda2  Extended  454.97MB
                                          /dev/hda5  Linux-swap   454.94 MB

I guess I'll have to reinstall with Manual partitioning instead of automatic.  The question is how do I specify partitions so that the boot ends up first on the drive so the BIOS can find it.??  Or can I simply repartition the existing install and move the boot forward via some commands in the Terminal??

Thanks for the help.

---

### Post by yabbadabbadont on 2007-04-07
The first partition should start at the front of the drive.  Just make it 256MB or so and it should completely fall within the 1024 cylinder BIOS limitation.  (of course, make it bootable and your boot partition ;))  You can do what you wish with the rest of the partitions since the BIOS doesn't need to touch them.  (and the linux kernel doesn't have the same limitations as the old BIOS)

---

### Post by kubobbu on 2007-04-07
Yabadabadont:  thanks for your reply.  Can I repartition the drive as it now stands, or do I need to manually partition it as you suggest and then reload Xubuntu.

And how do I make that first partition "bootable" and my boot partition... just by calling it that, or is more required.

Thanks..

---

