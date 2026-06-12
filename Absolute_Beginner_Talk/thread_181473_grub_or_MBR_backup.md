---
title: "grub or MBR backup"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by p1r0 on 2006-05-24
Hi

I have my computer set up  to boot with win98 or winxp or Ubuntu 5.10. The problem comes whe I have to format any of my window$ partition (you how win is format it every 6 month to have it woking properly ](*,) ). Then I cannot boot from any OS that is on to of it (win98->winXp->Ubuntu) and that is a real mess cuz I have to install all of them again if for instance I have to reinstall Win98.

What I want to do is to be able to back up the MBR before I format.

Thanks in advance.

p1r0

---

### Post by jorn on 2006-05-24
I assume your mswindows was installed on the first partition. That's where you probably have installed your grub bootloader.
So you must restore the bootlaoder every time your reinstall mswindows.
Otherwise you can install grub on  a floppy or another partition.

---

### Post by p1r0 on 2006-05-24
[QUOTE=jorn]So you must restore the bootlaoder every time your reinstall mswindows.[/QUOTE]
That's probably a good idea the thing is that I have no idea on how to do that.

[QUOTE=jorn]Otherwise you can install grub on  a floppy or another partition.[/QUOTE]
The floppy thing is probably not a good idea, but to install it on another partition sound iteresting but how will the system know where to find it??

---

### Post by Mustard on 2006-05-24
Have a read of the stuff at the bottom of this page for some idea of how you do it (backing up/restoring the MBR)
[http://www.partimage.org/Partimage-manual_Usage#Making_a_backup_of_the_partition_table](http://www.partimage.org/Partimage-manual_Usage#Making_a_backup_of_the_partition_table)

---

### Post by p1r0 on 2006-05-24
[QUOTE=Mustard]I have read of the stuff at the bottom of this page for some idea of how you do it (backing up/restoring the MBR)
[http://www.partimage.org/Partimage-manual_Usage#Making_a_backup_of_the_partition_table](http://www.partimage.org/Partimage-manual_Usage#Making_a_backup_of_the_partition_table)[/QUOTE]

Thanks I'll backup all data and give it a try.

---

### Post by jorn on 2006-05-24
I'm afraid I made a mistake. Your pc will allways direct you to the first partition on a drive, the MBR, You can't choose whatever partition you want.
I found a link that let you install grub with little effort.
[http://makuchaku.info/amnesty/#restoregrubmenuafterwindowsinstallation](http://makuchaku.info/amnesty/#restoregrubmenuafterwindowsinstallation)
It's probably the easiest way to solve your issue.

---

### Post by mlind on 2006-05-24
if you have floppy drive, using 'grub-floppy' is a easy way to backup boot loader
from MBR.

---

