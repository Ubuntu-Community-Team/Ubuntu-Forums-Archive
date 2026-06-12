---
title: "Installing vista after ubuntu"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-06-11
I had xp in my primary partition dual booting with ubuntu, however I deleted xp by mistake. What I was wondering was how should I intall vista on /dev/sda1 and than get grub back as I suppose vista will try and boot itself each time?

---

### Post by p_quarles on 2007-06-11
[COLOR=Black]I understand that people don't have much luck installing Vista after Ubuntu is on the system. If you need to install it, you should back up your Ubuntu data and /home folder to CDs/USB storage, then install Vista (this will wipe the drive). Then you can reinstall Ubuntu.

Also, I and a few other people have had luck with using the Vista partition manager to prepare a space for Ubuntu. Unsubstantiated rumors suggest that gparted might not get along with Vista. 
[/COLOR]

---

### Post by Najand on 2007-06-11
Just be careful not to remove your EXT3 and swap partitions and install it.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) works well for Vista too...

---

### Post by ugm6hr on 2007-06-11
> **ajeffreys said:**
> I had xp in my primary partition dual booting with ubuntu, however I deleted xp by mistake. What I was wondering was how should I intall vista on /dev/sda1 and than get grub back as I suppose vista will try and boot itself each time?

In theory, you could just install Vista on the prior XP partition without touching Ubuntu.  Then EasyBCD should enable you to access Ubuntu without GRUB.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Should admit I never bothered with it after doing the research, cos I wiped Vista in favour of XP, but I'm sure a search for it on google (or these forums) will find some people who have had success.

---

