---
title: "Noob question"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by squirl033 on 2007-03-29
i recently installed Edgy Eft on my PC... well, my son did, actually, after the OS-that-shall-not- be-named slowed to a crawl and had to be reloaded (there's another tale to that, but that's for another thread...). anyway, i went to turn on my PC this morning, and it got as far as the boot loader screen, loading GRUB. then it simply stopped, and said "Error 17". 

can someone tell me what "error 17" is? is it worse than 16? is my PC doomed? help!!! 
 
Rocky

---

### Post by phidia on 2007-03-29
See this thread: [http://ubuntuforums.org/archive/index.php/t-1669.html](http://ubuntuforums.org/archive/index.php/t-1669.html)

Also it would help to know hard drive(s) types (ide/sata) 

Sometimes going into bios and checking the boot order will fix this.

---

### Post by igknighted on 2007-03-29
When do you get the error?  After you select your OS to boot, or before you even get to the menu?

---

### Post by squirl033 on 2007-03-29
i don't even get that far. at present, i do not have XP loaded... only Ubuntu. it shouldn't ask me for a boot choice if Ubuntu is the only OS loaded, right?

---

### Post by annda on 2007-03-29
grub will always be there, since it is the bootloader needed to boot ubuntu. you can hide it (i mean the menu), but it will run at boot anyway.

if you had windows when installing ubuntu, and now you don't (if i understood you correctly), grub gets confused.

error 17 means that grub can see partitions defined in menu.lst but has a problem with them, specifically the filesystem.

sometimes it happens when linux is installed on a partition that is "too far away" from the boot sector - the beginning of the hard drive. but i think it happens only on older computers with old BIOSes.

if you boot from the live cd, can you post the output of fdisk? type this in the terminal (applications > accesories > terminal)

```
sudo fdisk -l
```

---

### Post by squirl033 on 2007-03-29
> **annda said:**
> grub will always be there, since it is the bootloader needed to boot ubuntu. you can hide it (i mean the menu), but it will run at boot anyway.

if you had windows when installing ubuntu, and now you don't (if i understood you correctly), grub gets confused.

error 17 means that grub can see partitions defined in menu.lst but has a problem with them, specifically the filesystem.

sometimes it happens when linux is installed on a partition that is "too far away" from the boot sector - the beginning of the hard drive. but i think it happens only on older computers with old BIOSes.

if you boot from the live cd, can you post the output of fdisk? type this in the terminal (applications > accesories > terminal)

```
sudo fdisk -l
```

thanks, Annda... 

i didn't have XP loaded when Ubuntu was installed. we wiped the HDs, and were planning to partition the smaller of the two and put Ubuntu in one part and XP in the other (there are still some photo-processing programs and such that Ubuntu won't support, so i need to keep XP around a while longer... ). we installed ubuntu, then tried to put XP in the other partition. it somehow wound up on the wrong hard drive, but it may still be messing up Ubuntu...  he was trying to set up my second HD with NTFS formatting, so i can use it as a data storage drive, and keep the OS's on my other drive. perhaps Ubuntu doesn't like having an XP filesystem on the same HD, even if it's in a different partition?  how do i make the error code go away, if i can't boot up? do i need to reinstall Ubuntu, or can i just boot from the CD and then correct the partitioning problem?

---

### Post by annda on 2007-03-29
you will most probably be able to correct any problems using the ubuntu live cd.

> perhaps Ubuntu doesn't like having an XP filesystem on the same HD, even if it's in a different partition?

oh, ubuntu has no problem with that. it just doesn' t like any major disk changes after install. any partitioning done after installation will cause grub to get confused and you will have to manually change it's configuration files. i know, it sounds a bit scary, but it isn't.

when you get to boot the computer from the ubuntu cd, post what the fdisk command tells you. this is very important to see what the problem is and what can be done to correct it, because it says how exactly all your disks are partitioned now.

after that, you will need to type a few more commands and everything should run smoothly.

---

### Post by squirl033 on 2007-03-29
thanks, Annda. i'm at work now, but when i get home, i'll dig into it and see what the fdisk command say, and let you know... appreciate the help!

---

