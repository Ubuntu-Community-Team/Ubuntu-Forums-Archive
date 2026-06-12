---
title: "FAT32 problem with external usb disk"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by alm on 2007-12-31
Hello and happy new year to the whole ubuntu "humanity" :lolflag:


After copying some files to a external usb fat32 disk, pulling the cable too soon (Ubuntu warning alert about unsafely unpluging things). 

Result: 

- **MacOS X** sees the disk but cannot mount it. When I verify it (translated to english from Disk Utility):
Verifying volume "LACIE"
** /dev/disk1s1
** Phase 1 - Read FAT
**Unable to read FAT (Input/output error)**
Error: The task has registered a fail at output
One volume no HFS checked
    The volume requires reparation

- **WinXP:** Sees the disk (letter F:) but cannot "mount" it. It goes extreeeemely slowly and finally says: **"Disk not ready"**.

- [B]Ubuntu: Sees and mounts the disk perfectly as usual, read and write just like if nothing happened.
[/B]

Trying to fix the "problem" so that mac and xp can mount correctly the disk I issued a dosfsk command:

xx@xx:~$ sudo dosfsck -r /dev/sda1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: ( offset:original/backup )
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
Got 22740992 bytes instead of 30517052 at 16384 
[*when not mounted:*]
Got 22798336 bytes instead of 30517052 at 16384
xx@xx:~$ 


Now I am so confused, so please correct me if I am wrong. I think that dosfsck tells me about two problems: "original/backup differences" and different number of bytes at 16384. **Am I wrong?**

**About the first dosfsck problem:** Being afraid of choosing 1 or 2 option (**how can I know which one is ok?**), I have search and found these sentences: 
dd if=/dev/sda1 of=sda1_block0.dat count=1 seek=0 skip=0 bs=512
for copying "original" fat to a file.
dd if=/dev/sda1 of=sda1_block6.dat count=1 seek=0 skip=6 bs=512
for copying "backup" fat to a file.

dd if=sda1_block0.dat of=/dev/sda1 count=1 seek=0 skip=0 bs=512
for copying a file to the main fat.
dd if=sda1_block0.dat of=/dev/sda1 count=1 seek=6 skip=0 bs=512
for copying a file to the backup fat.

I am thinking about copying the two FATs to a files, and then back. **But I am not sure if you can do that (copying with dd FATs to a files and back).**


**About the second dosfsck problem:** I am absolutely lost, no idea about what to do. Just tried with gnome partition editor, it shows a warning sign saying: "Got 22798336 bytes instead of 30517052 at 16384".

Any clues?

---

### Post by LaRoza on 2007-12-31
I would take all the data to safe place and reformat it.

It is possible to damage the cicuitry by pulling it out like that.

---

### Post by alm on 2008-01-02
Thank you very much LaRoza!

I totally agree with you, but the point is that I would like not to reformat the disk at the moment.
Thats why I would appreciate a** lot **if you could tell me something about the **FAT**.

---

### Post by LaRoza on 2008-01-02
> **alm said:**
> Thank you very much LaRoza!

I totally agree with you, but the point is that I would like not to reformat the disk at the moment.
Thats why I would appreciate a** lot **if you could tell me something about the **FAT**.

If Windows can see the drive, run chkdsk on it.

Format is:

```

chkdsk /F x: 

```

(Replace x with the drive letter)

---

