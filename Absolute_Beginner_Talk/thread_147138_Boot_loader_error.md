---
title: "Boot loader error"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Muttonz on 2006-03-19
Hi, me again.  After several frustrations, I successfully (or so I thought) got Ubuntu and XP running on the same harddrive.  I patched XP to Service Pack 2 and rebooted my computer.  It won't boot up, giving me this error message:
"GRUB Loading stage 1.5.

Error loading

Error 17"

I checked my BIOS and my boot order looks alright (cd, floppy, usb, then hd).  My hardrive is IDE.  From Googling around, I believe I need to use the live CD and boot into my new installation of Ubuntu and change something, but I'm not sure how and what.

Thanks for your help everyone.

---

### Post by Muttonz on 2006-03-19
Trying to help myself... but if someone could jump in that would be great.  Supposedly changing the mounts will fix this problem.  But which partitions should I change?

Here is what I have
NTFS partition (XP OS)
NTFS partition (for windows programs)
FAT32 part (for linux file storage)
Ext3 part (Ubuntu OS)
Swap part (for Ubuntu)

What mount should have what?

---

### Post by r4ik on 2006-03-19
This might fix it,
If unsure wait for someone to confirm.

[http://www.ubuntuforums.org/showthread.php?t=76652&highlight=MBR+messed](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=MBR+messed)

Good luck.

---

### Post by Muttonz on 2006-03-19
Yes, I've read that twice over and it still does me no good if I don't understand the instructions themselves.  

BTW, I've also tried the directions at [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)
specifically, the ones that say "Using the Live CD while preserving Windows bootloader."

---

### Post by Muttonz on 2006-03-19
I'd love to try the Super Grub Disk, but I can't find a working download URL yet.

---

### Post by r4ik on 2006-03-19
I will search for it also let you know asap.

---

### Post by Muttonz on 2006-03-19
All of the links I've found go back to the same broken link, d'oh!

Thanks for your help, r4ik, I appreciate it.

---

### Post by r4ik on 2006-03-19
The url seems to be of line at the moment i got it from Distrowatch Weekly,

[http://distrowatch.com/weekly.php?issue=20060313&mode=1](http://distrowatch.com/weekly.php?issue=20060313&mode=1)

The Super Grub Disk is almost at the end of the page,

[http://adrian15.raulete.net/grub/](http://adrian15.raulete.net/grub/)

So nothing usefull at the moment sorry.
Anybody else reading with suggestions please ?

---

### Post by r4ik on 2006-03-19
When i am not mistaking it can be found here,

[http://www.google.nl/search?q=Super+Grub+Disk&hl=nl&lr=&start=30&sa=N](http://www.google.nl/search?q=Super+Grub+Disk&hl=nl&lr=&start=30&sa=N),

The Super Grub should be on it.

[http://fileforum.betanews.com/detail/Ultimate_Boot_CD_Full/1066657762/1](http://fileforum.betanews.com/detail/Ultimate_Boot_CD_Full/1066657762/1)

Good luck.

---

