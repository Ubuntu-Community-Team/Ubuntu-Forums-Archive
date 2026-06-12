---
title: "Help with a portable USB hard drive"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Ob1 on 2006-03-28
I can just read from it, not write or execute. 

I can not change the permissions, but i am the owner.

(Unrealted to this problem: I have noticed how Ubuntu reads my portable USB hard drive much faster than Windows, sometimes Win XP would not even detect it)

---

### Post by aysiu on 2006-03-29
What filesystem is your USB drive? FAT32?

---

### Post by Ob1 on 2006-03-29
[QUOTE=aysiu]What filesystem is your USB drive? FAT32?[/QUOTE]

not sure probably NTFS

---

### Post by Ob1 on 2006-03-29
Since i can read the data on this Hard drive, what file system it is should not matter. Premissions is the problem.

---

### Post by trent dillman on 2006-03-29
What's your fstab entry look like for it?

---

### Post by Ob1 on 2006-03-29
[QUOTE=trent dillman]What's your fstab entry look like for it?[/QUOTE]

it is not listed there

---

### Post by Mustard on 2006-03-29
When its plugged in, can you show the output of this command please?

```
sudo fdisk -l
```

---

### Post by aysiu on 2006-03-29
[QUOTE=Ob1]Since i can read the data on this Hard drive, what file system it is should not matter. Premissions is the problem.[/QUOTE] To the contrary, it matters a lot. For example, if your USB hard drive is NTFS, read-only is all you can hope for, so there's no point in trying to figure out how to mount it differently.

Also, if it's FAT32, there are particular things you have to do to get it read/write--these particular things are different from what you'd have to do to get, say, Ext3 to be read/write.

Can you plug in the drive and then post the output of this command? ```
sudo fdisk -l
```

---

### Post by Ob1 on 2006-03-29
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7108    57094978+  83  Linux
/dev/hda2            7109        7296     1510110    5  Extended
/dev/hda5            7109        7296     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401    7  HPFS/NTFS

---

### Post by Mustard on 2006-03-29
Ok, the drive is NTFS and can't be written to from linux.  Linux will only mount it with read only permissions.  Is there any other issue with it mounting correctly, other than the read only problem?

If you wanted to reformat the drive in a FAT32 format you would be able to read and write to the drive. This would of course entail losing the data that is currently on it.  You would need to backup whatever critical data is currently stored on it.

---

### Post by Ob1 on 2006-03-29
[QUOTE=Mustard]Ok, the drive is NTFS and can't be written to from linux.  Linux will only mount it with read only permissions.  Is there any other issue with it mounting correctly, other than the read only problem?

If you wanted to reformat the drive in a FAT32 format you would be able to read and write to the drive. This would of course entail losing the data that is currently on it.  You would need to backup whatever critical data is currently stored on it.[/QUOTE]

Just the read only problem. But i'll have to back the files up somehow.

---

### Post by Ob1 on 2006-03-29
Ok, i have another Hard drive where i can store important data from the portable one, And my last question is how to i change it from NTFS to FAT32?

---

### Post by aysiu on 2006-03-29
Plug in the new hard drive. Make sure it's unmounted. Something like:
```
sudo umount /dev/sda1
``` should do the trick. You want the correct path, of course. If it's a slave drive, it may be /dev/hdb1.

Then ```
sudo apt-get update
sudo apt-get install ntfsprogs gparted
sudo gparted
``` The rest should be obvious, but if you have questions, post them back here.

---

### Post by Ob1 on 2006-03-29
Thanks for the help

---

