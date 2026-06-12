---
title: "CD/DVD drive locked when asking for reboot"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by zeusms on 2007-06-30
After running Ubuntu Live for a while, I decided to do an install to disk. The install is fine until it comes to reboot. My CD/DVD drive is now locked, and I can't remove the CD unless I press the reset button to restart the boot process. However, if I do that, Ubuntu fails to load and hangs with "GRUB loader stage 2". I then have to go into recovery console in XP to do a fixmbr, but then I don't have Ubuntu running unless I run it Live again. Of course, technically, the Ubuntu installation didn't complete, because the reboot didn't occur, and so I don't actually know if it would have started anyway. I don't understand why the CD/DVD drive should be locked. Any ideas?

(By the way, Ubuntu Server 7.04 installs perfectly... I've checked the media and it's fine).

Thanks in advance for any help, pointers etc

---

### Post by waggygee on 2007-07-04
Have you used this CD/DVD to install Ubuntu on any other computer? Its a possibility that the CD was not copied properly. Oh and when you attempt to open the drive, does the little light flash or the tray move or shake at all? (asking this to make sure it's not the tray that has problems

---

### Post by alienexplorers on 2007-07-04
Insert your live-cd and boot.  Open terminal and type sudo grub.
Enter:
> find /boot/grub/stage1
root (hd#,#)
setup (hd#)
quit grub
reboot

---

