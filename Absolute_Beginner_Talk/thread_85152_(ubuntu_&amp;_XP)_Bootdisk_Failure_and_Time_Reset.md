---
title: "(ubuntu &amp; XP) Bootdisk Failure and Time Reset"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by Tristan9669 on 2005-11-01
Everytime I bootup into ubuntu and restart or turn off my computer, right before the grub screen this comes up "BOOT DISK FAILURE, INSERT SYSTEM DISK AND PRESS ENTER." Luckly I have a bootdisk failure floppy disk that allows me to bypass this error message, but I tired of getting this error. Also everytime I'm in ubuntu and go back in xp my time gets all messed up and the hours change. Can anyone help me? :confused:

---

### Post by Kapre on 2005-11-01
[QUOTE=Tristan9669]Everytime I bootup into ubuntu and restart or turn off my computer, right before the grub screen this comes up "BOOT DISK FAILURE, INSERT SYSTEM DISK AND PRESS ENTER." Luckly I have a bootdisk failure floppy disk that allows me to bypass this error message, but I tired of getting this error[/quote]

I think this happens because you choose to use a floppy disk to boot your Ubuntu (meaning you did not install it in your MBR). You can get away with it by installing GRUB on your hard disk MBR.

>  Also everytime I'm in ubuntu and go back in xp my time gets all messed up and the hours change. Can anyone help me? :confused:

During the install you've selected to use the NTP clock. You can change it by reading this [thread]("http://www.ubuntuforums.org/showthread.php?t=76543&highlight=ntp+clock")

K

---

### Post by Tristan9669 on 2005-11-01
ok thanks, do I have to reinstall ubuntu to install grub, if not, how do I install it.

---

### Post by Kapre on 2005-11-01
[QUOTE=Tristan9669]ok thanks, do I have to reinstall ubuntu to install grub, if not, how do I install it.[/QUOTE]

Tristan - You dont need to re-install Ubuntu. You just have to install GRUB. See this [thread]("http://www.ubuntuforums.org/showthread.php?t=84865&highlight=install+grub") and only follow the part on installing GRUB using the LiveCD.

K

---

### Post by Tristan9669 on 2005-11-01
thanks alot :)!

---

### Post by Kapre on 2005-11-01
[QUOTE=Tristan9669]thanks alot :)![/QUOTE]

Youre more than welcome.

K

---

