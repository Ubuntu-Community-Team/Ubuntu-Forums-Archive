---
title: "HELP!!!! How do I get Vista working again."
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by kanati on 2007-07-20
I just installed ubuntu (feisty) and all is not well.  Ubuntu itself is working just fine (I'm using it right now) but now I can't boot into Vista.  Originally I was running a dual boot of XP and Vista.  Xp was installed on my Western Digital hard drive and Vista on the newer Seagate hard drive.  The plan was to replace XP with Ubuntu.  In the Ubuntu partition set-up I selected the option to install completely on a hard drive and selected the Western Digital drive.  Now when I set the bios to boot off the Western Digital drive I get and error saying that no operating system was found.  When I set it to boot off the Seagate drive I get Ubuntu.  Both hard drives are recognised in the file browser, one called "Filesystem" and the other called "WinVista" (the name I gave it when I installed Vista).  All my Vista files are still on the WinVista drive (Seagate) but I can't find a way to boot back into Vista.  I'm planning on switching over, but I'm not ready yet!!!

Thanks

PS.  I made a full back-up of my Vista drive before installing Ubuntu and I still have the Vista disk so I can do a full reinstall, but I'd prefer to avoid that if possible.

---

### Post by ReaderRat on 2007-07-20
*1) GRUB:  [[color=red]How GRUB Works[/color]](http://users.bigpond.net.au/hermanzone/p15.htm)
   2) Super GRUB Disk:  [*[color=blue]Super GRUB Disk[/color]*](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
   3) GRUB Manual:  [[color=red]GRUB Manual[/color]](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by kanati on 2007-07-20
"When IDE and SCSI (SATA) drives are used together it can mean some manual adjustments will need to be made."

Bingo,

Thanks

---

### Post by mulder_edu on 2007-07-20
Vista doesn't use the old boot.ini files.  Vista uses a database.  It's only backwards compadable with Windows.  I wasn't aware you could boot Vista with Ubuntu at all.  That may be your problem.
Microsoft doesn't particularly like open source :$

Sorry, I hope someone can prove me wrong.

---

### Post by benx009 on 2007-07-20
> **kanati said:**
> I just installed ubuntu (feisty) and all is not well.  Ubuntu itself is working just fine (I'm using it right now) but now I can't boot into Vista.  Originally I was running a dual boot of XP and Vista.  Xp was installed on my Western Digital hard drive and Vista on the newer Seagate hard drive.  The plan was to replace XP with Ubuntu.  In the Ubuntu partition set-up I selected the option to install completely on a hard drive and selected the Western Digital drive.  Now when I set the bios to boot off the Western Digital drive I get and error saying that no operating system was found.  When I set it to boot off the Seagate drive I get Ubuntu.  Both hard drives are recognised in the file browser, one called "Filesystem" and the other called "WinVista" (the name I gave it when I installed Vista).  All my Vista files are still on the WinVista drive (Seagate) but I can't find a way to boot back into Vista.  I'm planning on switching over, but I'm not ready yet!!!

Thanks

PS.  I made a full back-up of my Vista drive before installing Ubuntu and I still have the Vista disk so I can do a full reinstall, but I'd prefer to avoid that if possible.

see if [this website]("http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx") helps out.  a vista reinstall should really be a last resort; don't do unless u absolutely have to.

---

### Post by anarchyreigns on 2007-07-20
Not sure how to fix it with GRUB, however, I can tell you what happened, so that you'll know. When you installed Vista on the newer Seagate drive, Vista put its boot files on the first partition of the first disk, in this case, your Western Digital XP drive. When you later installed Ubuntu on that drive, it wiped out the Vista boot files. 

In the future, if you disconnect the other drive when installing, that won't happen.

---

### Post by confused57 on 2007-07-20
Since you have the Vista install disk, this may help:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by kanati on 2007-07-21
I just finished re-installing Vista on the Seagate drive.  A bit of a pain but thankfully I backed everything up.  Sadly I had Vista tweaked to perfection but I guess the tweaking must begin all over again.  I havn't tried getting back in Ubuntu yet (my system defaults to Vista now), that will wait until tommorow when I've recovered my patients.  I think I may have stumbled upon the best boot loader of all though.  When I tap F8during boot instead of getting the Windows boot menu I get a drive boot menu from the BIOS where I can just select the drive I want to boot off of (just like changing the priority in the BIOS).  Presumably if each OS has its own boot loader on its seperate hard drive then this should work, right?  I'm in no mood to try that out now but I have my fingers crossed.    

Thanks for the help,

---

### Post by kanati on 2007-07-21
> **anarchyreigns said:**
> Not sure how to fix it with GRUB, however, I can tell you what happened, so that you'll know. When you installed Vista on the newer Seagate drive, Vista put its boot files on the first partition of the first disk, in this case, your Western Digital XP drive. When you later installed Ubuntu on that drive, it wiped out the Vista boot files. 

In the future, if you disconnect the other drive when installing, that won't happen.

In retrospect that makes perfect sense.  I presume it didn't do that again since Vista won't even recognise the Western Digital drive in the drive list.  I assume that it just can't understand the Linux file system.

---

