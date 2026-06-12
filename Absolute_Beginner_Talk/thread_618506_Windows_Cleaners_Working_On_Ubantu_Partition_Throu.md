---
title: "Windows Cleaners Working On Ubantu Partition Through Ext2"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by sanford55 on 2007-11-20
Hi everyone.  I have a dual boot system with Gutsy and Windows XP. I installed Ext2 File System so I can see my Ubantu partition while in XP as an F drive.  I have discovered that when I run various cleaning programs while in XP, as well as my Norton anti-virus, they see into my Ubantu partition.  The cleaning programs find such things as tmp and bak and chk files, files I normally get rid of in windows.  Is it okay to let these windows cleaners operating from XP clean such files from Ubantu?   I suppose it would be a big mistake to let them do anything else, such as clean ubantu registry entries.  Thanks, Sanford

---

### Post by Inxsible on 2007-11-20
> **sanford55 said:**
> Hi everyone.  I have a dual boot system with Gutsy and Windows XP. I installed Ext2 File System so I can see my Ubantu partition while in XP as an F drive.  I have discovered that when I run various cleaning programs while in XP, as well as my Norton anti-virus, they see into my Ubantu partition.  The cleaning programs find such things as tmp and bak and chk files, files I normally get rid of in windows.  Is it okay to let these windows cleaners operating from XP clean such files from Ubantu?   I suppose it would be a big mistake to let them do anything else, such as clean ubantu registry entries.  Thanks, SanfordUbuntu and Linux in general does not have registry entries the way Windows does.

I would not allow any Windows based programs to delete anything from my Ubuntu partitions (at least not my home and root drives) That's why I havent even mounted them in my Vista. I only mount the shared partition which is EXT3 which has movies music etc. That way I am sure that Vista wont mess with my Ubuntu Os :)

---

### Post by petervk on 2007-11-20
I would also recommend that you do not allow the virus scanner to remove programs from the ubuntu disk. Use the ext2 windows driver as a convenience but try to not let windows or windows applications mess with your ubuntu partition.

A safer way is to have a third shared partition that both OS's can access (like a 1GB Fat32 partition) and stop using the windows ext2 driver. It's a nice tool but some windows virus or vulnerability could kill your ubuntu install.

---

