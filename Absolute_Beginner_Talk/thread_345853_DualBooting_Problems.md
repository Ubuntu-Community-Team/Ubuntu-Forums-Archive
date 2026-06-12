---
title: "DualBooting Problems"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Tr0n on 2007-01-24
I installed windows XP on my pc today and after the install I can no longer boot Ubuntu. I have Ubuntu installed on my primary and XP on my secondary. Any help will be greatly appreciated.

---

### Post by benuski on 2007-01-24
You're going to have to reinstall grub to the MBR, because when you installed Windows, it installed its own MBR.
If you go to [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") page, it will tell you how to reinstall grub.

---

### Post by Tr0n on 2007-01-24
So does that mean I want to preserve the bootloader, because it has instructions for overwriting also.

---

### Post by jbayone on 2007-01-24
I think you'll want to overwrite it.

---

