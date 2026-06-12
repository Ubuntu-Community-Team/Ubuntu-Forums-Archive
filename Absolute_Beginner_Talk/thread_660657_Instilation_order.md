---
title: "Instilation order?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by tylerdurden15 on 2008-01-07
I know you can install Linux on a system with windows already on it, but can I install either Windows XP or Vista on my PC with Linux on it?  I guess i could always just try and see what happens, one last question if i have both OS on my Pc can i easily get files from one to the other?

---

### Post by anewguy on 2008-01-07
You should install Windows first, as it will overwrite the boot sector and you won't be able to boot to Linux without going through a lot of extra work.

Yes, you can share data.  The easiest way is to set aside a Windows partition (preferably FAT32) to store those files in.  You can read/write to that partition from Linux.

Sharing data between Windows and Linux if the Windows partition is NTFS (the default for XP , etc.) is possible, but you need to install a special package.  The FAT32 method is an older more "proven" (forgive me you guys sharing NTFS!!:) ) method.

:)

---

### Post by tylerdurden15 on 2008-01-07
What kinda extra work? I already have linux the way i want it and dont want to have to go through reinstalling it.

---

### Post by nowshining on 2008-01-07
in linux - download from the repos gparted, create a parition, boot the XP CD, choose that partition, install, now since u want to install XP last, it doesn't play nice with the Grub bootloader, and so u'll have to go and search up on how to get it back up and running again, u can always use XP in a virtual machine such as virtualbox - it should be in the ubuntu repos.

---

### Post by anewguy on 2008-01-07
Yeah, wiping out the boot sector as I mentioned is the problem with loading Windows second.  You can download a copy of the ISO for the super grub disk - it will help you recover the boot sector.  I think you can also do the same thing somehow of the LiveCD you used for installation.  

See this thread for all you need to know after you install Windows (with Ubuntu already on your system), assuming you had the free partition space:

[http://ubuntuforums.org/showthread.php?t=659157&highlight=restore+grub]("http://ubuntuforums.org/showthread.php?t=659157&highlight=restore+grub")

:)

---

### Post by doorknob60 on 2008-01-08
Yeah, the super grub disk does the job and it's pretty easy to use from what I've heard. Also Gusty has NTFS support built in and I've had no problems with it :)

---

### Post by bwtranch on 2008-01-08
Re #6 Yeah, when I used to do a dual boot. That worked. I don't do that anymore, though. Every machine has it's own OS and that really works better. I know, not everybody can have a machine for every OS that they want. If I had just one machine and only one OS, I would have to pick Ubuntu. or excuse me maybe Windows 2000, that is a good one. Too bad MS couldn't keep that going. The stuff they put out now is garbage.

---

### Post by anewguy on 2008-01-09
> **doorknob60 said:**
> Yeah, the super grub disk does the job and it's pretty easy to use from what I've heard. Also Gusty has NTFS support built in and I've had no problems with it :)

Nice to hear that on the NTFS front!  Maybe I'll take the chance and put Windows XP back on this old dog PC.  Thanks!:)

---

