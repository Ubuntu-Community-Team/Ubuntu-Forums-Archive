---
title: "xp/ubuntu DB. NO choice on reboot! goes to windows directly!"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by manij on 2007-09-01
I have a dimension 3100 160G SATA HD.

I wiped out the recovery partition and the intial dell utility partition and manually configured the partition such that I left the XP installation alone and installed dapper. The installation is successful however, upon reboot, I do not the choice of operating systems and it directly boots to XP.

Is this a GRUB problem? 

I did the same thing on my t'pad R51 with any problem and am posting from it using ubuntu!

Help!

---

### Post by Seti on 2007-09-01
Pop in the liveCD and read your grub conf file, its probably set to just boot to first OS on the list.

---

### Post by meborc on 2007-09-01
are you sure you INSTALLED grub? ... to the MBR?

it sounds to me you are missing it... since the windows bootloader starts up... if you had grub, then it should boot to ubuntu by default...

this should work in your case as well (don't get discouraged by the title :)) [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

---

### Post by Gone fishing on 2007-09-01
I usually put the grub on the linux partion and use GAG [http://gag.sourceforge.net/](http://gag.sourceforge.net/) as the boot loader this makes it very easy to choose which OS to boot first Ubuntu, XP BeOS etc

---

