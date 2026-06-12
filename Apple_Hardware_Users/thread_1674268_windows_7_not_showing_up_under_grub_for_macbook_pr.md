---
title: "windows 7 not showing up under grub for macbook pro"
date: 2011-01-23
forum: Apple Hardware Users
---

### Post by xinfamousx101 on 2011-01-23
Hi all
 
I am trying to triple boot osx, win7 and ubuntu 10.10 on my macbook pro. This is the way I did it:
 
-Installed osx and created 2 partitions in disk utility, one for osx and another formated as dos fat to manually hybritized my drive and allow for windows installation (the new bootcamp is currently messed up, so can't do it that way).
 
-Installed win7 by bio booting the cd, and deleting the formatted partition (dos fat) and creating a new one via win installation.
 
-Installed ubuntu by bios booting the cd and creating its own partition in setup.
 
Now, when I turn on my macbook and press alt, 2 icons come up, mac and windows (so good so far!). But when I go into the windows option, grub loads and I see 5 entries:
 
-Ubuntu
-Ubuntu safe mode
-Memtest
-OSX 32 bit
-OSX 64 bit
 
Obviously osx is not going to boot under bios boot. But where is win7 that should be in the list?!?!
 
Thanks for any help!

---

### Post by furok23 on 2011-01-23
bump
same problem.
grub hates us lol

---

### Post by xinfamousx101 on 2011-01-24
fixed it!
 
instead of creating partitions as you install each OS, use disk utility during the first os install (mac osx) to create ALL of the partitions (mac, windows, ubuntu and data with all of them being dos fat except for the mac partition). Then during windows and ubuntu installations, just take the partitions you already created and reformat (NOT DELETE) them.
 
Why it works? I am not exactly sure. But I did notice that during windows installation, instead of making two partitions (one MBR and one windows), it only made one. And I think it migrated into the MBR partition that osx created as the emulator.
 
Cheers :DD

---

