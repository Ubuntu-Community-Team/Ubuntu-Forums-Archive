---
title: "dual boot with 7.10 use NTFS or FAT32?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by sagesparrow on 2007-10-03
I am just getting ready to set up a dual boot system with XP Pro and Ubuntu.  The plan is to have at least one separate partition for files, email boxes, etc. that will be shared by both XP and Ubuntu.  This was going to be FAT32.  But should I set it up as NTFS in anticipation of Ubuntu 7.10 which is supposed to have read/write capability with NTFS?  Or just go with FAT32?  What are advantages of each?

Also, does having files on separate partition affect the performance/speed of accessing files?

Thanks

---

### Post by js_fr on 2007-10-03
I would choose NTFS, because
- it is a more modern file system as FAT, e.g. you don't have such strict limitations with file size (I think ~2GB is the maximum for FAT32). 
- Ubunty 7.04 also supports NTFS, you only have to install the ntfs-3g package. A detailed description how to do this you can find here: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G) 

Concerning performance - I think if your XP / Ubuntu system partition is installed on a different hard disk as the data partition you will have better performance in parallel access. If they are an the same hard disk I don't think so ... but in general it is a good idea to have the data on a separate partition :)

---

### Post by sagesparrow on 2007-10-03
thanks

---

### Post by glinsvad on 2007-10-03
Agreed, fat32 sucks and is very slow. On the upside, it's supported by just about any operating system and disk image/ghost software.

---

### Post by js_fr on 2007-10-03
Concerning disk image / ghost software and FAT / NTFS - I use SystemRescueCD which ...
[LIST]
[*]is based on linux and free
[*]contains GParted (partition resizing) and Partimage (backup) which can both handle ext2,3 / NTFS / FAT ...
[*]many other useful things like X (if you don't like the command line) and Samba - so that I can store the backups directly on my file server :)
[/LIST]
I use it to backup both my (last and only) Windows and Linux installations. You can download it here: [http://www.sysresccd.org](http://www.sysresccd.org)
The only place where I still have FAT are partitions encrypted with truecrypt ([http://www.truecrypt.org](http://www.truecrypt.org)) ... until they really support ext2/3

---

### Post by bodhi.zazen on 2007-10-03
You can use ext3 

There is a windows driver here : [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by sagesparrow on 2007-10-03
What would be the advantages of using ext3?

---

### Post by stchman on 2007-10-03
> **glinsvad said:**
> Agreed, fat32 sucks and is very slow. On the upside, it's supported by just about any operating system and disk image/ghost software.

FAT32 is no slower or faster that other file systems.  The only real downside to using FAT32 is the 4GB file size limitation.

---

### Post by js_fr on 2007-10-03
Cool, I didn't know that there is a driver for windows which can write ext2 :)
So in principle you have the choice between NTFS and ext3 (and FAT). I would say your choice depends on how you plan to use your system. Do you work more often with Linux? Then I would choose ext3 ...
ext3 has also the advantage that it is a journalled file system which gives you extra security against data loss in case of a crash ... though, you don't have this advantage when you access it from windows with the driver bodhi.zazen suggested.

---

### Post by bodhi.zazen on 2007-10-03
> **sagesparrow said:**
> What would be the advantages of using ext3?

ext3 is open source 

If you use primarily Linux, go for ext3

If you use primarily Windows, go for ntfs

If you don't know, go for FAT

That way, if you have problems, you can use the tools you are most familiar with to fix them ...

---

### Post by master_kernel on 2007-10-03
NTFS, becuase there is automatic write support in 7.10.

---

