---
title: "Dual Boot System (Yaboot) is not working any more."
date: 2006-07-03
forum: Apple PPC Users
---

### Post by Najand on 2006-07-03
I have installed and I were using Dapper Drake 6.06 on an iBook G4 and suddenly the dual boot system is not working any more. I used to boot MacOS X (Panther 10.3.9), Linux (Ubuntu 6.06) and the CD-ROM Drive, but suddenly the dual boot system is not working and the system just boots MacOS X. I don't know much about Yaboot. Anyone can help me recover the Linux and my Data on ext3 drive?
I would appreciate any helps.

---

### Post by calum on 2006-07-03
[QUOTE=Najand]I have installed and I were using Dapper Drake 6.06 on an iBook G4 and suddenly the dual boot system is not working any more. I used to boot MacOS X (Panther 10.3.9), Linux (Ubuntu 6.06) and the CD-ROM Drive, but suddenly the dual boot system is not working and the system just boots MacOS X. I don't know much about Yaboot. Anyone can help me recover the Linux and my Data on ext3 drive?
I would appreciate any helps.[/QUOTE]

Hold down the Option key while you boot, that should show you your bootable partitions, one of which should be Linux.  If so, select it to boot from it; otherwise, boot from your Ubuntu install CD and look for the 'rescue' option.

Either way, once you're back in Linux, you probably just need to run 'sudo ybin' to re-write the boot loader onto your disk.  Usual caveat: back up everything you care about before you try this, in case things go horribly wrong.

---

### Post by Najand on 2006-07-03
[QUOTE=calum]Hold down the Option key while you boot, that should show you your bootable partitions, one of which should be Linux. [/QUOTE]

Thank you very much. It works exactly as you said. And I could restore boot loader onto my disk. I maybe should learn more about Apple Macintosh Systems.

---

### Post by Uta on 2006-07-03
That happened to me also and all I did to fix it was zap my PRAM and on restart I had my dual boot back.

---

### Post by [D-Man] on 2006-10-05
Yes...

See [http://ubuntuforums.org/showthread.php?p=1553722#post1553722](http://ubuntuforums.org/showthread.php?p=1553722#post1553722)

---

