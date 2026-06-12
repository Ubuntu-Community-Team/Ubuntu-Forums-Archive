---
title: "I can now access my hard drive, How do i enable it so i can delete stuff off it"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by morbidAUS on 2007-03-15
hey, i can access my hard drive but I am unable to delete stuff from the hard drive... it says 
```
""/media/sda... 4.mp3.sfk" cannot be deleted because it is on a read-only disk."

```

Then when i go to change the properties it says
```
"Sorry, couldn't change the permissions of "111.8 GB Volume: sda1".
```
I need to be able to delete stuff so i can free room and burn stuff of my hard drive before i wipe it... thanks in advance

---

### Post by Najand on 2007-03-15
> **morbidAUS said:**
> hey, i can access my hard drive but I am unable to delete stuff from the hard drive... it says 
```
""/media/sda... 4.mp3.sfk" cannot be deleted because it is on a read-only disk."

```

Then when i go to change the properties it says
```
"Sorry, couldn't change the permissions of "111.8 GB Volume: sda1".
```
I need to be able to delete stuff so i can free room and burn stuff of my hard drive before i wipe it... thanks in advance

Is it a NTFS drive? If so you cannot delete anything from it as far as it just mounts in ReadOnly Mode.
Check it out if it is ntfs or not by the "mount" command or "sudo fdisk -l" command.

---

### Post by morbidAUS on 2007-03-15
damn it... its an ntfs drive... sighh... i guess i wont be able to burn ill just have to use a portable hard drive to copy the data.... anyway thanks for your help i appreciate it...

---

### Post by hyper_ch on 2007-03-15
there are drivers that can write to ntfs.. however I would be careful in that manner. If something will not work correctly you may loose all your data on the ntfs drive.

However you have other options. You can use a shared fat32 partition so both windows and linux can read/write there or you could install the ext2/3 drivers in windows. In that case windows will be able to read/write to your linux partitions.

---

