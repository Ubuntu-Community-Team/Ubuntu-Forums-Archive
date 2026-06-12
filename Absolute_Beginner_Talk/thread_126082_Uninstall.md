---
title: "Uninstall"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Don M on 2006-02-05
How do I uninstall ubuntu and grub
without damaging windows xp?
thanks Don M

---

### Post by o_fortuna on 2006-02-05
[QUOTE=Don M]How do I uninstall ubuntu and grub
without damaging windows xp?
thanks Don M[/QUOTE]
You should be able to reclaim the hard-disk space from within windows. Just click start, run, and type diskmgmnt.msc at the command line, and find the partition you want to format. I've never done this, but it should work. On the other hand, I don't have the slightest clue how you'd go about getting rid of grub.

---

### Post by Cousindaddy on 2006-02-05
To remove GRUB, you can boot Windows from your installation CD (like you did installing Ubuntu) and select "R" for repair.  Select the correct option: for me it was "1. C:\Windows".  Then, from the prompt (C:\Windows) type "FIXMBR"  This stands for Fix Master Boot Record.  It takes a bit but it worked fine for me.

---

### Post by Don M on 2006-02-09
[QUOTE=o_fortuna]You should be able to reclaim the hard-disk space from within windows. Just click start, run, and type diskmgmnt.msc at the command line, and find the partition you want to format. I've never done this, but it should work. On the other hand, I don't have the slightest clue how you'd go about getting rid of grub.[/QUOTE]
I tried to use diskmgmnt.msc and system said unable to locate.
A search also turned up nothing
Is there any other way to un install ubuntu on a xp duel boot system?

---

