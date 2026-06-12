---
title: "Possible to install dual boot with Ubuntu x86?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-03-04
Hello! :]
Does anyone know if its possible to have dual boot with windows and ubuntu x86? I know when installing the 64bit version, there was a scroller which set the amount of space that Linux would use, but installing with the x86 version, that option doesn't seem to exist.

There are some other options in it's place, but those don't seem to be the solution :/

TIA!:confused:

---

### Post by Joeb454 on 2008-03-04
You need to partition the drive so it has some free space first :)

Also the installer for x64 and x86 machines are exactly the same (except the bits ;)) I should know, I've used both :D

The above is true, unless you got the alternate installer by accident :)

---

### Post by Kevbert on 2008-03-04
It is possible. You need to select manual partitioning to add your new main and swap partitions.  Your main partition should be formatted ext3.
With windows you may have a paging file towards the end of the drive. Run the Windows Defragmentation Program and defrag the drive. If this block of data has not been moved you'll need to turn off this file. It can be found at Control Panel - System - Advanced Tab. Now click on Settings under Performance and select the Advance Tab. Now click on Change, the Virtual Memory paging file and select the No Paging File radio button. No click on Set, OK, OK, OK and close Control Panel.
Reboot the machine and then defrag the hard disk again. There should now be extra room at the end of the disk.
Don't forget to back everything up.

---

### Post by hungryOrb on 2008-03-04
thanks for the replies :]
What happened when installing the ubuntu 64 version, was that my hard disk had a single partition with windows on, then ubuntu simply asked me how much of the hard drive (in percentage) that I wanted to assign to linux and then it created the new partition for me. 
I'm guessing after reading the second reply,. that it had this option, because there was space at the 'end' of the disk? If so thanks, I'll try that :D

---

