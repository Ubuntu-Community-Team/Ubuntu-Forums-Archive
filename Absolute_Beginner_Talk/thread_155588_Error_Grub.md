---
title: "Error Grub"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by jbraum on 2006-04-05
I rebooting my computer and am getting the following error message.

GRUB loading, please wait...
Error 17

Here's my setup to help.  
I have Unbuntu on my secondary drive and Win XP on my primary.  I need to be able to boot windows because the computer is my wife's and she doesn't want or like Linux.  So I would also like to remove Linux from the secondary hd and keep windows.  Any help would be great.

---

### Post by pbaehr on 2006-04-05
If you don't want to keep Ubuntu the best way to fix it would probably be to boot from the Windows XP setup disk, enter the recovery console and use 'fixmbr' to flush out Grub entirely. I've never tried it myself, but I believe this will cause Windows to boot as normal and from there you should be able to wipe the secondary drive.

---

### Post by meborc on 2006-04-05
there is a wikipage about recovering grub [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

---

### Post by jbraum on 2006-04-05
[QUOTE=meborc]there is a wikipage about recovering grub [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)[/QUOTE]

dev/discs/disc0/partX , where the X is a partition number

I get 3 different partition numbers and an error when I try to do the next step with each of them


Can I restore from the live cd?

---

