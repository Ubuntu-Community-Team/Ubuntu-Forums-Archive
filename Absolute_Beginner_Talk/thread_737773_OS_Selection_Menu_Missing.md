---
title: "OS Selection Menu Missing"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by steelisreal on 2008-03-27
I currently have 2 320gb harddrives one with xp and one with ubuntu.

The ubuntu hd is the slave.

I had a major issue and had to reload XP and now my OS selection screen is missing so I can't get to Ubuntu.

I tried searching but couldn't really find anything on how to restore this menu.

Maybe you could help me with this issue, and maybe how I could have searched better.

Thank you

---

### Post by Rocket2DMn on 2008-03-27
That menu is called the GRUB boot menu, and it was bypassed when you reinstalled windows which took over the MBR.
Here you go - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
It's OK to overwrite the windows bootloader.

---

### Post by Joeb454 on 2008-03-27
You need to reinstall GRUB, perhaps [this link]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") will help you :)

It's really not all that complicated to do :) I had to do it a few weeks back

---

