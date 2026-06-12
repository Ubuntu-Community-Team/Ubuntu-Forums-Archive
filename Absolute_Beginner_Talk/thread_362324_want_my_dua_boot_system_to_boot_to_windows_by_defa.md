---
title: "want my dua boot system to boot to windows by default"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by cmk_78212 on 2007-02-15
I have a dual boot set up with edgy.  When I start up, it gives me a list of options of OS's to run.  Ubuntu is the 1st option, so if I do nothing, it boots to Ubuntu.  I would like XP to be the first option and thus boot XP by default.  

This is my boot file in windows:
[boot loader]
timeout=7
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

Any ideas?

---

### Post by bollix47 on 2007-02-15
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by NeonShadow on 2007-02-15
I'm assuming you are using GRUB, if so, you need to edit /boot/grub/menu.lst

Make sure to make a backup of it before you change anything.

following command should get you there:

```
sudo gedit /boot/grub/menu.lst
```

you need to change ```
default 0
``` to what ever number down the list your windows is, first line being 0.

---

