---
title: "Blank screen after entering startx command in backtrack 5"
date: 2012-05-21
forum: Any Other OS
---

### Post by seenu4uever on 2012-05-21
Hi.

I got blank screen after entering startx in backtrack5.

I have tried to remove the .kde files but it says no directory found. Also after changing the grub file, then update-grub is not working. it says " error: cannot find a device for / (is /dev mounted?" Please reply to [EMAIL="srinivasan.infotech@gmail.com"]{deleted} [/EMAIL]Thanks in advance.

---

### Post by oldfred on 2012-05-21
Welcome to the forums.

Was in old thread on chroot, moved to own thread, old thread for ref:
[http://ubuntuforums.org/showthread.php?t=1517144](http://ubuntuforums.org/showthread.php?t=1517144)

Removed direct email link to prevent spam. Use forum for responses.

I would not delete files.

Were you chrooting into your install? That is normally the last resort before a reinstall. You can usually fix grub2 boot issues with this:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

And then is grub boots to menu (or if only one system, hold shift key from BIOS to get menu.) then it may be video issues.

---

