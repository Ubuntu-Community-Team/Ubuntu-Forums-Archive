---
title: "Using Ubuntu for file recovery"
date: 2005-09-01
forum: Absolute Beginner Talk
---

### Post by sasmyth on 2005-09-01
Ubuntu (actually Knoppix, but I only have a Ubuntu cd right now) was suggested to me to recover some files from a computer that windows has died on.  I have used the live version of the cd and successfully booted Ubuntu.  My problem now is I can't seem to find my old files from windows that I wish to recover.  Any suggestions?

Thanks!

---

### Post by KingBahamut on 2005-09-01
mount the drive to a folder on your system. I think the LiveCD has ntfsprogs enabled. 

so just do an 

mkdir /mnt/ntfs
mount -t ntfs /dev/hdx /mnt/ntfs

where hdx is the drive that is your windows drive. 

then browse the /mnt/ntfs directory.

---

### Post by sasmyth on 2005-09-01
ok these are probably really stupid questions, but I have never used linux at all before.  

1.  where do I type this?  (I am pretty sure the answer is the command line, but I actually don't know where the command line is)

2.  in the commands you gave me I am supposed to substitute my drive instead of hdx--if my drive is C  is this what it shoudl look like?

mkdir /mnt/ntfs
mount -t ntfs /dev/C /mnt/ntfs

Thanks so much

---

### Post by UbuWu on 2005-09-01
[QUOTE=sasmyth]ok these are probably really stupid questions, but I have never used linux at all before.  

1.  where do I type this?  (I am pretty sure the answer is the command line, but I actually don't know where the command line is)

2.  in the commands you gave me I am supposed to substitute my drive instead of hdx--if my drive is C  is this what it shoudl look like?

mkdir /mnt/ntfs
mount -t ntfs /dev/C /mnt/ntfs

Thanks so much[/QUOTE]

1. Applications -> System tools -> terminal

2. Your c drive is probably /dev/hda

Also you will have to type sudo in front of mount.

---

