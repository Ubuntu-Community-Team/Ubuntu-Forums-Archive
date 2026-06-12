---
title: "bizarre dual boot situation on Ubuntu Studio/win XP"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-09-18
I have a dual boot system winXP and ubuntu studio; however, if I boot from cold into ubuntu, the boot hangs at initramfs. If I boot into XP and then reboot, Ubuntu studio comes up quite happily, and everything works. If I reboot from Ubuntu- to see what happens- it hangs again. I have no idea where to look for an explanation and  a solution to this, but I don't like having to boot up winXP to get to ubuntu. Any ideas, anyone?

---

### Post by notwen on 2007-09-18
Are you using GRUB or the Windows Boot-loader?

---

### Post by ginestre on 2007-09-18
> **notwen said:**
> Are you using GRUB or the Windows Boot-loader?

-GRUB, loading UbuntoStudio (Feisty) or win XP SP2. I have loads of disk and ram.

---

### Post by notwen on 2007-09-19
initramfs is pre-kernel loading, I'm not knowledgeable enough to assist you with an issue involving initramfs.  Wikipedia has a small article about it [here]("http://en.wikipedia.org/wiki/Initramfs").  I'm not sure if re-installing the kernel would be a fix for this or not.  Good luck with this issue, and please post back should you learn anything new to resolving your issue.

---

