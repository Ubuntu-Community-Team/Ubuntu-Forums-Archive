---
title: "Reinstalling XP on dual boot with Ubuntu"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by mortuk on 2007-06-25
Hey all, just need a quick answer to my Q if thats cool.

I have XP dual booted with Ubuntu and want to know if I reinstall windows is that going to mess up Grub?

---

### Post by kevinlyfellow on 2007-06-25
It will undoubtedly mess up grub, so you should be prepared to fix that.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation)

Or if you just want to use your livecd 
[http://www.arsgeek.com/?p=655](http://www.arsgeek.com/?p=655)


If you need more, just search for "restore grub" 

In case it was unclear, the numbering scheme works like this
(hd0) means the first harddrive
(hd0, 0) means the first partition of the first harddrive.

If you have anymore questions, just ask

---

### Post by munkydust on 2007-06-25
Yes if you reinstall windows it will write over Grub. After you have installed windows, you need to put the ubuntu CD in a reinstall grub.

---

### Post by linhtinh321 on 2007-06-25
> **munkydust said:**
> Yes if you reinstall windows it will write over Grub. After you have installed windows, you need to put the ubuntu CD in a reinstall grub.

Firstly, I install Win XP, then install Ubuntu. After that, I restore Win XP, but the Grub is okie. I don't need to change anything.

---

### Post by Golyadkin on 2007-06-25
> **linhtinh321 said:**
> Firstly, I install Win XP, then install Ubuntu. After that, I restore Win XP, but the Grub is okie. I don't need to change anything.

yes, but that is not the question :) The situation is that both Ubuntu and XP are already installed, but that the poster wants to reinstall XP. Because XP (like any other Windows version) doesn't tolerate other operating systems, it overwrite the bootmanager, because it wants Windows to rule supreme :)
To reverse this, you need to reinstall GRUB, so you can boot into Ubuntu again.

---

### Post by steve-shinn on 2007-06-25
This all presupposes that the poster is dual booting off 1 hard drive....clearly the answer would be differnet it he was dual booting off 2 hard drives ie XP on 1 and Ubuntu on the other.

---

### Post by kevinlyfellow on 2007-06-25
> **steve-shinn said:**
> This all presupposes that the poster is dual booting off 1 hard drive....clearly the answer would be differnet it he was dual booting off 2 hard drives ie XP on 1 and Ubuntu on the other.

It doesn't matter, since windows will reset the mbr.  The grub re-installation process will be the same, but with different numbers (like root could be (hd1,0))

---

