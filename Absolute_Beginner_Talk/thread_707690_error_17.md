---
title: "error 17"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Jack Moore on 2008-02-25
Hello Everyone !!!    HELP !!   I cannot get the boot choices to come up on screen befor the mach. locks up and I get msg that says (boot loader error 17)  Its locked to that page and nothing works except for the curser blinking.  I  just loaded ubuntu 7.10 onto a win xp machine and all went fine.  Third time I booted it crashed.  I tried to rerun over top of the old program with my install disk and it stops dead near the end of the process.  I had no time to make any boot disks befor crash and I'm so new to Linus that I flipped a coin to see which version to try.   I have a ten year old mach with 768 megs of ram and a ten Meg Hd.  It was working, tho very slow on the linus side.  I can get into the cmos on startup and I saw three partitions listed there but could not tell which was windows.  I thought I might delete Ubuntu and start windows then reload Ubuntu, but I really need help      Thks    Jack

---

### Post by A4006 on 2008-02-25
First of all... It's Linux, not Linus.  Grub error 17 : Cannot mount selected partition, means that Grub found the right partition, but it cannot recognize the file system.  As for which partition is which, the windows file system is NTFS (for XP at least).  Try reinstalling Grub with the LiveCD or resetting the MBR to the Windows boot loader if you no longer want Ubuntu.  Oh, and I think you mean that you have a 10 GB hard drive instead of 10 MB...

---

### Post by Forrest Gumpp on 2008-02-25
See if this post helps:  [http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9)

This is the link to Herman's GRUB page on his Illustrated Dual Boot site:  [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)  It provides many links to GRUB related resources, as well as good general information.

You mention that your computer is an older one.  You may well have a BIOS limitation in which the BIOS is unable to interact with the boot files if they are not within the first 8.37 GB of the HDD.  I understand that this condition can lead to GRUB Error 17.

If that does turn out to be your problem, and you are unable or unwilling to upgrade your BIOS, you may be able to get around it by obtaining another HDD and installing Ubuntu on that.  That would ensure that the GRUB files would be within the first 8.37 GB of the disk.  Ubuntu can be installed upon, and booted from, a slave HDD.  Used HDDs are relatively inexpensive at computer markets these days.

---

### Post by Jack Moore on 2008-02-27
Hey    I want to thank you both for all the advice.  The reinstall worked after several trys.  I think Linus liked the fact that I gave it the whole HD.   It set up on my third try when I finally gave up on xp.  I really did'nt know what I was doing but with your help it went well.  I think I'll just enjoy it for a few days and then tackle my modem.  Thanks again for all your help.    Jack:KS        :)

---

