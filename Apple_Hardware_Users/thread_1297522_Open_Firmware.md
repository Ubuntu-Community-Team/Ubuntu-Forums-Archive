---
title: "Open Firmware"
date: 2009-10-21
forum: Apple Hardware Users
---

### Post by fslezak on 2009-10-21
I know this has nothing to do with Ubuntu, but I want to fix it.

Whenever I boot the machine, I always end up with the Open Firmware screen. This never happened before I enter the command to continue, but HOW do you stop it from interrupting my normal boot?

Thanks for your help.

---

### Post by lgerbarg on 2009-10-26
It could be a couple of things. Since you don't say what command you type to boot, I am not sure why it isn't booting. The simplest thing to check is that it is set to auto-boot.

At the firmware prompt try typing:

setenv auto-boot? true
reset-all

The first line sets the auto-boot? variable to true, which is what the firmware checks to determine whether to stop in open firmware are attempt to execute the boot-command. The second tells open firmware to reboot your computer, which will also cause it to commit any pending nvram changes. At that point it should reboot, and hopefully go directly to your bootloader.

There is also a chance you are set to boot put one of your boot parameters is wrong and it errors out, then you are manually typing in something valid.

---

