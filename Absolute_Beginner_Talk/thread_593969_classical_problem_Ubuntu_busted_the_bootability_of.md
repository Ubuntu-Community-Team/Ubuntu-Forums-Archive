---
title: "classical problem: Ubuntu busted the bootability of my WinXP"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by loldrup on 2007-10-27
I know that others solved it by editing the boot.ini when booted in Ubuntu, but my problem is that I can't find the boot.ini-file on my WinXP NTFS-partition. Where is it supposed to lie?
I can't find it when searching other winXP-computers either.

I have tried booting a WinXP rescue CD and then "bootcfg /rebuild" but that fails.
That's why I'm trying to edit the boot.ini manually.
Anyone know where it lies?

/Jon Loldrup

---

### Post by thelocust on 2007-10-27
How did Ubuntu mess with your boot.ini file in XP. Are you sure your not just having a GRUB problem?

---

### Post by loldrup on 2007-10-27
Okay, you are right - Ubuntu didn't mess with it, but Windows got confused by the resizing of the partition. I have to replace '1''s with '2''s in the boot.ini

When I boot I get the GRUB menu, but when I choose Windows XP it says it's missing a hal.dll-file.
I have enshured that this file is not corrupt. The problem is the boot.ini. This guy has a similar problem:
[http://ubuntuforums.org/showthread.php?t=414393](http://ubuntuforums.org/showthread.php?t=414393)

my only problem is I can't find this damn file so I can edit it. Ubuntu reads my Windows XP NTFS-drive fine.


/Jon Loldrup

---

### Post by thelocust on 2007-10-27
[check it out.]("http://support.microsoft.com/kb/289022")

---

### Post by kellemes on 2007-10-27
> **loldrup said:**
> Okay, you are right - Ubuntu didn't mess with it, but Windows got confused by the resizing of the partition. I have to replace '1''s with '2''s in the boot.ini

When I boot I get the GRUB menu, but when I choose Windows XP it says it's missing a hal.dll-file.
I have enshured that this file is not corrupt. The problem is the boot.ini. This guy has a similar problem:
[http://ubuntuforums.org/showthread.php?t=414393](http://ubuntuforums.org/showthread.php?t=414393)

my only problem is I can't find this damn file so I can edit it. Ubuntu reads my Windows XP NTFS-drive fine.


/Jon Loldrup

As far as I remember you can use the Windows-disk recovery-console to fix the bootstuff.
I think it's "FIXBOOT" but if you type HELP in the console you'll see it.
Could very well be it won't scream about hall.dll if you fix boot.ini etc..

---

