---
title: "Wanting to remove GRUB (but not for Windows)"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by quoick on 2007-01-07
I have recently installed ubuntu exclusively on a machine that used to contain both WinXP and ubuntu. Consequently it has GRUB installed that I want to remove as I think it may be causing an intermittent freeze error. I have searched these forums and found [this ]("http://www.ubuntuforums.org/showthread.php?t=147291&highlight=remove+grub")post but since I don't intend on ever installing Windows on this machine again it is not quite what I am after. If anyone could help it would be greatly apprecitated.

---

### Post by mahy on 2007-01-07
you can restore the original windows bootloader without reinstalling windows. Just boot the windows installation cd, select the recovery console and enter "FIXMBR" command. That's the only way...

EDIT: wait a sec, you don't have windows and you wanna remove GRUB? then you'll have to install something else, e.g. LILO. Is that what you want?

---

### Post by kinematic on 2007-01-07
without grub or another bootloader you can't boot at all ;)

---

### Post by quoick on 2007-01-07
Cheers. From what I had read it seemed that GRUB was for dual booting. Sorry to have been such a newb.

---

### Post by louieb on 2007-01-07
There are other  boot loaders available. LILO and GAG come to mind first and I am sure there are others. Check the dual boot link in my signature. Herman has some nice stuff on some of the various boot loaders. The thing is GRUB is the most widely used and the easiest on to get help for.

---

