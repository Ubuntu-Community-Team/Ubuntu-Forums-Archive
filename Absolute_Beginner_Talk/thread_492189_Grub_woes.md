---
title: "Grub woes"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by blueorder on 2007-07-04
I use Windows XP and wanted to dual boot XP and Ubuntu.

I have a 75GB primary SATA drive that ubuntu install sees as **hde** and an IDE 120GB data drive that ubuntu install sees as hda.

I resized the drive XP is on (hde) and created the following partitions:

mount Windows partition as /windows (hde1)

swap --> 3GB
/ --> 20GB
/home --> 27GB

After install, I rebooted and it went straight into Windows XP without showing GRUB on POST.

I reinstalled, and clicked on advanced on the review screen and saw that the drive to install GRUB was designated as **(hd0)** which I figured is my data drive as it is seen as hda. I switched (hd0) to **(hd1)** and after install/reboot, GRUB popped up on POST but after selecting Ubuntu and error appears saying something to the effect of "cannot find partition" and if I ESC back to menu and select Windows XP it shows an error saying that it cannot find NTLDR.

Any suggestions?

TIA

PS. A little about me. I'm computer literate and know my way around the command prompt. Used Ubuntu before; just never seen this GRUB issue.

---

### Post by confused57 on 2007-07-04
> **blueorder said:**
> I use Windows XP and wanted to dual boot XP and Ubuntu.

I have a 75GB primary SATA drive that ubuntu install sees as **hde** and an IDE 120GB data drive that ubuntu install sees as hda.

I resized the drive XP is on (hde) and created the following partitions:

mount Windows partition as /windows (hde1)

swap --> 3GB
/ --> 20GB
/home --> 27GB

After install, I rebooted and it went straight into Windows XP without showing GRUB on POST.

I reinstalled, and clicked on advanced on the review screen and saw that the drive to install GRUB was designated as **(hd0)** which I figured is my data drive as it is seen as hda. I switched (hd0) to **(hd1)** and after install/reboot, GRUB popped up on POST but after selecting Ubuntu and error appears saying something to the effect of "cannot find partition" and if I ESC back to menu and select Windows XP it shows an error saying that it cannot find NTLDR.

Any suggestions?

TIA

PS. A little about me. I'm computer literate and know my way around the command prompt. Used Ubuntu before; just never seen this GRUB issue.

What you can try is to highlight your Ubuntu entry in your grub boot menu, press "e", highlight the line with root, press "e" again, then change root from (hd1,x) to (hd0,x), press "enter", then "b" to boot...this change is temporary, but can be made permanent in your /boot/grub/menu.lst, if it works.

---

