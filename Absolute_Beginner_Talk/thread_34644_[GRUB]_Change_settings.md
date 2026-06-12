---
title: "[GRUB] Change settings"
date: 2005-05-15
forum: Absolute Beginner Talk
---

### Post by Stekkie on 2005-05-15
Hi

I've a problem. When I installed Ubuntu and I reboot my PC, Grub will load. The standard OS is then Ubuntu. I found at the internet how I can change that, but not where. So... where can I find the configuration file?

A second problem, when I had too much troubles with Ubuntu/Grub, I decided to format that partition (in WinXP), after rebooting Grub gave an error and I couldn't  start up anymore... also WinXP. So i needed to format both partitions and re-install WinXP. How can I fix that problem in the future?

A thirth problem, can I install another bootloader?

A bit offtopic but too stupid to open a new thread:

Ubuntu doesn't see any NTFS-partitions. Someone told me Ubuntu must see them. How can I fix that?

Thanks!

(Sorry for my bad English : O:)  ;-) )

---

### Post by monchichi on 2005-05-15
First Problem: refer to [this thread](http://ubuntuforums.org/showthread.php?t=34393) 

Second Problem: You could avoid this program by not formatting the partition in Windows.

Third Problem: You could use lilo, but it isn't as good as grub in my opinion.

NTFS problem: is there a line for your NTFS partition in your /etc/fstab file?

---

