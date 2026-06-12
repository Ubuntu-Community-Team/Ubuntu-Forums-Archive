---
title: "DualBoot Kubuntu/WindowsXP standby problem"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by siggi2 on 2007-07-18
Hi all,

I am learning Linux using Kubuntu 7.04 in dualboot on a PC with Windows XP Home. I did set GRUB's menu.lst such that at bootup WinXP will start within 3 seconds if no Kubuntu choice has been  made. This is just not to confuse the other less experienced, still Windows, user – I call him userWin here. Works fine, except... when userWin causes a shutdown due to a long standby! 

In pre-Kubuntu-times, userWin just hit the PC's start-button, WinXP was booting , and after log-in he was in his previous pre-standby Windows session. 

Now with dualboot WinXP/Kubuntu, after hitting the start button, BIOS comes up first, requires the BIOS-Admin-password, then the upcoming menu asks "where do you want to boot from? – harddrive, floppy, cdrom?". Choosing the harddrive finally does the correct dual boot, i.e., bringing up WinXP or Kubuntu, depending on either waiting 3 seconds or choosing Kubuntu. This whole BIOS stuff confuses userWin.

How can I help him to avoid this complicated BIOS menu business afte a standby?

Thank you,

siggi2

---

### Post by siggi2 on 2007-07-19
i found my own solution. Disabled BIOS Admin password. Apparently, this is the BIOS security sacrifice I have to make to live in both worlds :(

---

