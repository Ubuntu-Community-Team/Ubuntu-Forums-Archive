---
title: "GRUB error 17"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-02-04
After removing Ubuntu (reformatting the partitions) I now get "Error 17" when grub appears on the screen... 
I'm using the Live CD to access the forum.
How may I correct this so that I can boot normally into XP?
Thanks for your help.

---

### Post by Klaidas on 2006-02-04
You could restore grub using this tutorial: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Cousindaddy on 2006-02-04
Thanks for the reply...actually, I fixed the problem by rebooting with the XP install disk in the default drive typing "R" for repair, and then "fixmbr" for fix master boot record.
It seems to have worked.

---

### Post by cotcot on 2006-02-05
By removing ubuntu you removed the grub menu, stage1 and stage 1.5 (located in the ubuntu /boot/grub), so the grub boot loader in the MBR could not find it.

---

