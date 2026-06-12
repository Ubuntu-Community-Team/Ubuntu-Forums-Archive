---
title: "Grub Issue - Error 19"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-07-15
I had a dual-boot with WinXP and Ubuntu.  Since I've been enjoying the linux experience, I decided to put an additional distro on there.  I installed OpenSuse just to see what it was about.  Unfortunately, OpenSuse didn't include Ubuntu in it's load menu.  It only has Windows and Suse.  So, I went into the boot loader editor in Suse, and tried to add Ubuntu (I know it's still on the hard drive), and then the loader took Suse off the list, and just had Windows, and Ubuntu, except when I choose ubuntu, I get an "Error 19: Linux kernel must be loaded before initrd.  Obviously, I've messed it up even more, but I can't figure out what to do next.  I thought that maybe using Super Grub would work, but the site seems to be down and I can't download it.  

Any suggestions? I'd like all three OSs on the menu.  Thanks.

---

### Post by HappySnowflake on 2007-07-15
Yeah... you were right to go with openSuSE.  Ubuntu just can't handle preloaded operating systems very well.  I recently covered up a MBR murdered by Ubuntu by installing openSuSE just to get my XP back.  Stick with openSuSE and forget trying to use Ubuntu to solve your problems.  Ubuntu only creates problems, hence this forum...

---

### Post by thefoolisme on 2007-07-15
I appreciate your feedback, but it doesn't help my problem.  I'd like to fix grub to list all 3 OSs.  Thanks.

---

### Post by confused57 on 2007-07-15
You could reinstall Ubuntu's grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then you should be able to add a configfile entry to Ubuntu's menu.lst to boot Suse:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

