---
title: "Dual Boot - Can I edit which OS boots by default?"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by Katandrea on 2005-09-28
My husband has no interest in computers other then playing Spider in Windows XP :)   Since I have installed Ubuntu - he does not like having to learn the steps to scroll down to WinXP and hit enter - and he wants to know if there is a way I can make WinXP boot by default after the choice menu - when no choice is made.

This way he can boot my computer while I am at work without having to deal with the menu.

Is this possible? 

Thank you,

Kathy

---

### Post by mlomker on 2005-09-28
If you open the /boot/grub/menu.lst you'll find that the file is pretty well documented.  There are a couple settings that you can change in there.

---

### Post by Vulpus on 2005-09-29
[QUOTE=Katandrea]My husband has no interest in computers other then playing Spider in Windows XP :)   Since I have installed Ubuntu - he does not like having to learn the steps to scroll down to WinXP and hit enter - and he wants to know if there is a way I can make WinXP boot by default after the choice menu - when no choice is made.
This way he can boot my computer while I am at work without having to deal with the menu.
Is this possible? 
Thank you,
Kathy[/QUOTE]

First of all you need to:

sudo gedit /boot/grub/menu.lst 

Look for a line that says something like (I am away from my Ubuntu pc so can't check) :

Default: 0

You need to change that number to another 'suitable' number to select the default OS.  What number you need depends on the boot list.  So if your grub boot screen looks something like:

Linux kernel
Linux Kernel (safe mode)
Mem test
Win XP

 you need to choose the number 4 to boot XP by default.  That is because the numbering starts at zero AND the line of text (divider) before the Win XP listing in the menu.lst file is counted as an entry.  

Thus:

0: Linux kernel
1: Linux kernel(safe mode)
2: Mem test
3: other operating systems
4: Win XP

Hope that helps?

An alternative solution is to get your husband to play the psider equivelant on Ubuntu?

---

### Post by mp3guy on 2005-09-30
Or you could wait a few days for breezy, or even dist-upgrade now and get the graphical bootmanager

---

### Post by mlomker on 2005-09-30
> graphical bootmanager

You mean the one that was just removed because it has serious bugs?  There are other threads about that online today.

---

### Post by lovestopsfear on 2005-10-02
i answered my own question....
can't figure out how to delete this reply....

---

### Post by joelito on 2005-10-02
Must have been a kernel upgrade, I think you have to create a new windows entry
```

title		Windows 
root		(hd0,0)
chainloader	+1
savedefault

```

Or something like that...

And BTW. Make sure you create a backup menu.lst next time

---

