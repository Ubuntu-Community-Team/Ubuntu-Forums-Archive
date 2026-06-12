---
title: "I installed windows, now I can't boot into Ubuntu anymore"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by æþeling on 2006-05-29
So ussualy when I boot, I'd get the menu where you select which OS to boot, bot I've recently had to reinstall windows, and now that menu doesn't appear, when I turn the PC on it just starts loading XP right avay, thus preventing me from booting into Ubuntu (or any other OS). What should I do?

---

### Post by Mau on 2006-05-29
You need to re-install Ubuntu (the easist way).  Windows doesn't like other non-Windows operating systems.  You have to install Windows FIRST, and then any other operating system.

---

### Post by qamelian on 2006-05-29
[quote=Mau]You need to re-install Ubuntu (the easist way).  Windows doesn't like other non-Windows operating systems.  You have to install Windows FIRST, and then any other operating system.[/quote] 
No need to reinstall. Just follow the instructions found at:
[http://doc.gwos.org/index.php/Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

That should do the trick.

---

### Post by æþeling on 2006-05-29
what if I don't have a /boot partition (and no free space for it)?

---

### Post by aysiu on 2006-05-29
[QUOTE=æþeling]what if I don't have a /boot partition (and no free space for it)?[/QUOTE] What do you need a /boot partition for?

---

### Post by ghostwalk.with.me on 2006-05-30
[QUOTE=æþeling]So ussualy when I boot, I'd get the menu where you select which OS to boot, bot I've recently had to reinstall windows, and now that menu doesn't appear, when I turn the PC on it just starts loading XP right avay, thus preventing me from booting into Ubuntu (or any other OS). What should I do?[/QUOTE]

Quick question: what version of Ubuntu are you running? And the version of Windows, is it an OEM or did it come on the backup cd that came with your computer?

---

### Post by æþeling on 2006-05-30
ghostwalk:
Ubuntu 5.10; Windows XP pro, I bought it on a CD seperate from my computer.

aysiu:
it says I need it in that tutoial

---

### Post by mostwanted on 2006-05-30
[QUOTE=æþeling]ghostwalk:
Ubuntu 5.10; Windows XP pro, I bought it on a CD seperate from my computer.

aysiu:
it says I need it in that tutoial[/QUOTE]

If you haven't made a /boot partition, that folder will just be a subfolder to / - the reason the tutorial tells you to mount /boot is because some people do keep that folder in its own separate partition, but you don't so you can just mount the other partitions it tells you to mount.

---

### Post by catlett on 2006-05-30
You don't need to reinstall. Follow the guide. As already stated don't worry about the boot partition. This is a little tricky if you're not used to linux yet.
The directions will tell you to put the install disk in and follow the procedures. When you get to partitioning you're going to select the ubuntu partitions. I don't know how you formatted but if you did a simple install it will only show / and swap. You might have done a little more advanced and then it will be /, swap and home. Either way the partitioner will have them labeled.
You want to select the ubuntu partitions and then DO NOT FORMAT them. You will be given a choice. Just choose all the ubuntu partitions but choose to leave them unformatted and save the data. Choose to save the partitioning scheme or write changes to disk (I forget) it will come up with  a prompt that it can't install. You will hit continue until you end up with a menu with about 20 lines. Go down to install grub boot loader. It should install grub and then exit.
Microsoft did that to me before. It doesn't tell you it is overwriting the mbr. Good luck. Just trying to clarify a bit.

---

### Post by æþeling on 2006-05-30
Great, thanks for the help, got the GRUB menu back now.

---

