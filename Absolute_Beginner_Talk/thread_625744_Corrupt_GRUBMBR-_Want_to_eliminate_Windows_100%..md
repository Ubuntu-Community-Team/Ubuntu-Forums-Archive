---
title: "Corrupt GRUB/MBR- Want to eliminate Windows 100%."
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by lstellar on 2007-11-28
*Sorry if this was posted earlier. I have found people with similar problems, but not the same. And the same solutions do not seem to work.

About six months ago I installed Ubuntu on my XP machine with a normal dual boot + GRUB. Everything worked fine up until about two weeks ago when my offices' antivirus software (in XP) caused my swap/boot partition to go corrupt.

Initially, the first time I restarted my PC I received GRUB Error 15. I left it alone for a while since it was kind of nice to be "unplugged." Yesterday I attempted to re-partition the entire drive using the Ubunutu LiveCD into a Linux partition. After the reboot post partition and installation, I no receive "Loading Stage 1.5... GRUB Error 22" (or something close).

Whats unique to my issue, I think, is that I DO NOT CARE ABOUT XP. I am done with Windows all together, and if possible, I want to avoid using an XP CD, RecoveryConsole... anything associated with Windows. So here are my goals:
1. Fix/eliminate MBR and boot ONLY to Ubunutu. 
2. Resize entire partition to erase Windows partition. 
3. Reformat if necessary (what file type for Ubuntu? partition name? etc...)
4. CD only- no floppy drive on my laptop. 
5. Do this is as cleanly as possible.

Is this all possible with a regular Ubuntu LiveCD? Do I need something else? Let me know...

Thanks ahead for the help. Also fell free to get a hold of me at [email]lstellar@gmail.com[/email]

Thanks.

-L

---

### Post by ukripper on 2007-11-28
use super grub to fix your MBR - [http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

and then boot from live cd and use gparted to completely delete your XP and merge your partion with your current installation of ubuntu partition.

all goals achieved.

---

### Post by lstellar on 2007-11-28
Thank you sir. Hope I am not back here tonight pleading for more help.:(

---

### Post by ukripper on 2007-11-28
> **lstellar said:**
> Thank you sir. Hope I am not back here tonight pleading for more help.:(

Even if you back for help dont hesitate to post in forums someone will surely help! :)

---

