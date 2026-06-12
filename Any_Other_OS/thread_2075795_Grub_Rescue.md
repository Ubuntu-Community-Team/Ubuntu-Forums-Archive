---
title: "Grub Rescue"
date: 2012-10-24
forum: Any Other OS
---

### Post by jaggernought on 2012-10-24
I want to install windows 7 again on my laptop, currently it had Ubuntu on. Because boot form disk or USB isn't working I had to remove the hardrive, attatch it to my PC and install windows 7 that way. But now when I boot my laptop I get the message "error: unknown file system" and the grub rescue. What can I do to boot windows 7 ?! :(

---

### Post by oldfred on 2012-10-24
Moved to OtherOS since a Windows issue.

If Windows was installed correctly it would overwrite MBR.

But I do not think you can install Windows from one computer onto a drive for another computer. It is licensed for one system only and will recognize it is on a different system. It probably installed its boot files to the computer you used to install.

You can from Windows install a new MBR or from Ubuntu liveCD or USB install a Windows like boot loader, but I do not think that resolves your issue.  I think you have to boot from CD or USB to install Windows. 

You can install Ubuntu from one PC onto a hard drive and then use it on another if you do not install any proprietary drives that may be incompatible.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


As far as installing Windows you can ask on Windows formums.

[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

---

