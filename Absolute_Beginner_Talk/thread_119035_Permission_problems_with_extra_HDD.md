---
title: "Permission problems with extra HDD"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by TumbleWeed on 2006-01-18
ive got kubuntu installed on the primary master (a 20gb disk) and an 80gb disk from an XP machine (NTFS format) with all my music on it. the problem is that i cant delete or create anything on it because i cant change the permissions. in my attempts to allow r/w permissions i set the permissions of the block device and /storage folder to allow for everyone. when the disk is mounted to /storage i go into its settings i cant change the permissions from 
User: Can view content
Group: Forbidden
Others: Forbidden
cause it gives me a not enough permission access.

this is all in root and all that. ive tried dozens of different fstab configurations and the current one is
/dev/hdb1 /home/sbrian/storage ntfs rw 0 0

if someone would be kind enough to assist me in my quest, i shall grant them three wishes.

Love From Sam.

---

### Post by jonathanm on 2006-01-18
try adding users to your fstab:
/dev/hdb1 /home/sbrian/storage ntfs rw,users 0 0

---

### Post by frodon on 2006-01-18
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by TumbleWeed on 2006-01-18
well id like for either of those suggestions to aid me, but really, it hasnt. except i have an idea..

nls=utf8,umask=0222

that changed the access permisions and set everything to "Can view only", so if someone would be kind enough to tell me what to set it so i can read and write, that would be INSANE. i tried adding in rw in the options but it didnt do any good. the problem is at where the drive is mounted, and its properties. it says
"Could not change permissions for /home/sbrian/storage" if i try to change anything.

Love From Sam

---

### Post by frodon on 2006-01-18
NTFS don't support unix rights and ownership that's why you will never be able to change permissions on a NTFS partition. In addition you have to know that your partitiion is read-only because there's no write support for NTFS under linux that's why many peoples here prefer using FAT32 or ext3 instead of NTFS.

---

### Post by ajgreeny on 2006-01-18
Surely this is because linux can only read from but not write to ntfs disks and you will not be ablt to write in any way to this file system.  To do so you would need your winxp disk or partition to be formatted in fat32, not ntfs.

---

### Post by TumbleWeed on 2006-01-18
i was afraid of something such. what a silly filesystem.
you came closest to fixing my problem, so you get three wishes... but only after you throw me back in the water.

---

### Post by frodon on 2006-01-18
Yes it's really annoying especially for people who try to move to linux, this is due to microsoft because it don't want to share informations on how NTFS is made so that's why there's no reliable write support under linux.

FAT32 file system could be a good solution for you if you wish to use both windows and linux because it has write/read support with both OS.

---

