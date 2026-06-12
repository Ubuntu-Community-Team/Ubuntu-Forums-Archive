---
title: "[SOLVED] Doomed dual-boot scenario or what?"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by offline on 2007-09-24
SCENARIO OF AN OLDER NEWBIE

Let's say that I do the following:

1)Let windows 2000pro sit in the first NTFS disk of my pc untouched 

2)Do a simple delete on every data in my second FAT32 disk

3)Reboot using Ubuntu  6.06 Live CD 

4)Do an automatic  install of ubuntu  to the second disk( just choose 2nd drive to install automatically and wait)

**[COLOR="Red"]What's going to happen when finally I reboot?[/COLOR]**

a)Will there be a choice screen  to choose windows or linux?

b)_Or this is doomed?_

Note that it's not crucial for me(I think) that I exchange data/interact between 1st drive and second directly. I can move files(pictures, docs, txt, html, music, videos) back and forth using a usb flash stick

Can you advice please?

---

### Post by overdrank on 2007-09-24
Sounds like  A is the correct answer. :popcorn:

---

### Post by Shazaam on 2007-09-24
Shouldn't be any problems. You may have to install video drivers and network card drivers if you want to run 3d apps and do wireless.
After you reboot a boot screen (grub) will open allowing you to chose which OS you want to load.
A stock install of Ubuntu will mount your Windows partition READ ONLY allowing you to copy files from it. To get write access you can install a number of tools (search the forums). You can also install drivers in Windows that allow write access to your Ubuntu partitions. I do NOT recommend the latter because Windows CAN trash your Linux OS. If you want to do that I recommend a separate partition that both Windows AND Ubuntu can read/write to that has NO critical files on it.

---

### Post by offline on 2007-09-24
Thanks. 

> **Shazaam said:**
> 
A stock install of Ubuntu will mount your Windows partition READ ONLY allowing you to copy files from it.

You mean, when in Linux I can copy from windows partition only but when in windows I can read and write on the first disk as usual?


 > **Shazaam said:**
> I recommend a separate partition that both Windows AND Ubuntu can read/write to that has NO critical files on it

In the second disk, in FAT32 form? Can this be done by choosing... "shrink a little" button in ubuntu installation or I have to do it manually?

---

### Post by Shazaam on 2007-09-24
> **offline said:**
> Thanks. 



You mean, when in Linux I can copy from windows partition only but when in windows I can read and write on the first disk as usual?

 

In the second disk, in FAT32 form? Can this be done by choosing... "shrink a little" button in ubuntu installation or I have to do it manually?

1.Yes. Windows will not change because it natively doesn't recognise linux partitions. Linux recognises quite a few. In XP it will show the disks in Disk Management (as unrecognised) but no where else. Thats why you need to install tools to  Windows  to allow read/WRITE access to Linux disks/partitions from Windows.

2. Depends on the partitioning type. During install Ubuntu will give you a choice of types. You can do custom partitioning to add a partition (and format it to whatever you like eg. NTFS, FAT32, ext3, etc) for your needs or you can do a default install and resize later. The fun part of Ubuntu is you can let it guide you with an install or you can pop the hood so to speak and tweak it any way you want. You aren't restricted like you are with Windows. Do a bit of reading on the forums and you will find many opinions on what to do.

---

