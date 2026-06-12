---
title: "Uninstalling Ubuntu.."
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by F3nr1L on 2007-01-18
I recently built myself a new computer. My old one is going to my mother, who can't honestly understand the difference between ubuntu and windows. I have both a Windows XP Home and a Ubuntu 6.10 partition.

So my question is, how do I completely remove the Ubuntu partition?

---

### Post by shane2peru on 2007-01-18
your best bet would to be reinstall windows XP and it will overwrite Ubuntu.  If you just delete the partition you will have problems because Grub will look there for your boot loader.  I know there is some way to fix your windows boot loader, but I'm not sure of that process.  If you find that you can delete the Ubuntu Partition (format it as ntfs, or fat32) from a Live Cd and then restore XP boot loader and you are all set.

Shane

---

### Post by kinematic on 2007-01-18
if you're mother won't know the difference why not keep ubuntu ;) 
if you decide to reinstall win xp format the partition first....i've seen weird things happen when people install one os over another.

---

### Post by bswilson on 2007-01-18
You can delete that partition, and then quite easily repair your Windows boot loader by removing grub.  If you uninstalled a Linux partition and get "stuck" at a grub prompt, then enter these commands to boot into another OS that is loaded on your hard drive.

```
rootnoverify (hd0,0)
makeactive
chainloader +1
boot
```

In Windows XP, you can permanently uninstall GRUB as follows:
[LIST]
[*]Boot from the Windows XP CD and press the "R" key during the setup in order to start the Recovery Console.
[*]Select your Windows XP installation from the list and enter the administrator password.
[*]At the input prompt, enter the command "FIXMBR" and confirm the query with "y".
[*]The MBR will be rewritten and GRUB will be uninstalled.
[*]Press "exit" to reboot the computer.
[/LIST]

In Windows 2000, you can permanently uninstall GRUB as follows:
[LIST]
[*]Boot from the Windows 2000 CD and press the "R" key during the setup and the "K" key in the following menu in order to start the Recovery Console.
[*]Select your Windows 2000 installation from the list and enter the administrator password.
[*]At the input prompt, enter the command "FIXMBR" and confirm the query with "y".
[*]The MBR will be rewritten and GRUB will be uninstalled.
[*]Press "exit" to reboot the computer.
[/LIST]

---

### Post by bodhi.zazen on 2007-01-18
> **bswilson said:**
> You can delete that partition, ....

Very nice post :p

---

### Post by F3nr1L on 2007-01-18
I would keep it ubuntu except she would notice the difference when she couldn't click on the taskbar. :P

Thanks. However, I don't have a Windows CD, so is there a way to fix it without the CD?

---

