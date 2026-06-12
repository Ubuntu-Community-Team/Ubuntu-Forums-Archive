---
title: "Having huge problems mounting fat32 drive"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Magimog on 2007-02-05
I have just installed Ubuntu with major issues on my HP nc4000 (no cdrom :) ) and managed to get that going fine. I have split my 40 GB hdd into 3 partitions, 5GB SYS, 2GB Swap, and the remaining in a fat 32 partition. 

I have tried many many guides on this to no avail... here is the error I'm getting:

> mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Here is my fstab line for my fat32 (hda3):

> /dev/hda3     /media/windows     vfat     defaults,umask=0000     0  0

Can anyone help me? I'm completely lost :(

---

### Post by comfurtn on 2007-02-05
> **Magimog said:**
> Here is my fstab line for my fat32 (hda3):

Can anyone help me? I'm completely lost :(

Your fstab line looks fine, although the "umask=0000" might be causing the problem... replace the line with the following:

> /dev/hda3 /media/windows vfat defaults,utf8,umask=007,gid=46

---

### Post by Magimog on 2007-02-05
No go :( I ran the DMESG command and here are some interesting lines:

> [17179809.816000] FAT: invalid media value (0x7c)
[17179809.816000] VFS: Can't find a valid FAT filesystem on dev hda3.
[17180017.748000] FAT: invalid media value (0x7c)
[17180017.748000] VFS: Can't find a valid FAT filesystem on dev hda3.

Here is my FDISK log as well:
>    Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         650     5221093+  83  Linux
/dev/hda2             651         780     1044225   82  Linux swap / Solaris
/dev/hda3             781        4864    32804730    b  W95 FAT32

The ID = b kinda throws me off... but I'm not sure


I formatted the drive using the Ubuntu installer.  Is there a program I can use to possibly reformat hda3 and try again?

---

### Post by comfurtn on 2007-02-05
If you have no data on the drive that you want to keep, then you can install gparted using synaptic.. and then reformat the drive.

---

### Post by Magimog on 2007-02-05
Found it! Looks like my FDISK log was lying to me... I do fondly remember setting the format to fat32 on install, but it was read as "unknown". Everything is fine now. Many thanks comfurtn!

---

### Post by comfurtn on 2007-02-05
Not a problem!  Glad you got it to work! ):P

---

