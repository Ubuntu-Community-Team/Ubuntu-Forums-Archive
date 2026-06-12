---
title: "Using fsck"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by noeluylee on 2006-02-01
I am using Kubuntu Breezy with KDE 3.5

I want to run fsck manually. as per fsck man, I tried, fsck.ext3 -f /dev/hds6
this msg appears:
e2fsck 1.38 (30-Jun-2005)
/dev/hda6 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

should I unmount it? say if i should, how can I unmount the /dev/hda2 (/root)? i that poosible? i mean im working on the computer i guess /dev/hda2 should not be unmounted. also with /home?

I tried sudo fsck -f /dev/hda6 
this appears:
noel@Noel:~$ sudo fsck -f /dev/hda6
fsck 1.38 (30-Jun-2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:44/00, 72:41/00, 73:54/00, 74:41/00, 75:20/00, 76:20/00, 77:20/00
  , 78:20/00, 79:20/00, 80:20/00, 81:20/00
1) Copy original to backup
2) Copy backup to original
3) No action


by the way, what is the difference of fsck and fsck.ext3?

Thanks.

---

### Post by Herman on 2006-02-01
```
sudo touch /forcefsck
``` 
The way I do it is to type the above code into a terminal and then reboot my computer. When the computer is re-booting, if you watch carefully, you will see it pause during the boot-up sequence and do the fsck for you before it fininshed booting, that way the filesystem isn't mounted yet I presume. It looks like this (Below)
|============================                                          /

You will see the white '=' signs progress across the black screen until they reach the tumbling bar '/'. Sometimes it might stop and announce it has found a problem and fixed it. (It will often give details). 
Ubuntu will do an fsck automatically every thirty reboots anyway, you don't have to do it manually, but it shouldn't do any harm and might do some good.:-D (Herman)

---

### Post by noeluylee on 2006-02-01
Thanks a lot herman.. Really appreciated it. :-) will try this. :D

Noel

---

