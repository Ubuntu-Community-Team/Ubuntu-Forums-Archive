---
title: "Dual boot question, Linux first Windows second."
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by tylerdurden15 on 2008-01-07
I already have Linux installed and want to install Vista on my machine for a dual boot. My hard drive is already partitioned, am I gonna have a problem putting vista on second? Someone already said i will not be able to boot Linux any more if i do it that way, if so what would be the fix for this?

Thanks in advance!

---

### Post by mister_pink on 2008-01-07
When you install windows it will overwrite Grub (the bootloader that gives you the menu). The solution is to install windows, then reinstall grub, for which I think you'll need a bootable cd. I've seen supergrub suggested before, but I imagine you can do it from an ubuntu live cd. Someone should write a windows utility for fixing it really....

Edit: See here [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by tylerdurden15 on 2008-01-07
Awesome thanks, i was actually reading that thread, just didnt know if it pertained to windows as well.

Thanks Again

---

### Post by tylerdurden15 on 2008-01-07
i am currently running 7.04 but have the bootable cd from 6.10 that will not be a problem correct?

---

### Post by mister_pink on 2008-01-07
Shouldn't think it would be a problem, but I'd wait for someone else to confirm it. I've not been using ubuntu that long so I'm not sure if the version of grub has changed much in that time.

---

