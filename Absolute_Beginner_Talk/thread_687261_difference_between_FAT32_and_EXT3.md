---
title: "difference between FAT32 and EXT3"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by marnie6771 on 2008-02-04
Something strange is happening here: I am converting my cd collection to flac on a 500 Gig internal Hitachi SATA hard disk. For safety I am constantly making backups of my work on an external Lacie 500 Gig hard disk. The Hitachi is formatted in EXT3 and the Lacie is FAT32. Both have an identical directory structure and exactly the same amount of stored data: 395 GB. Only the the LaCie says to have another 100 GB of free space and the Hitachi only 40 GB. Does anybody know why this is? 

Many thanks in advace and kindest regards from

Marcel

---

### Post by jd65pl on 2008-02-04
A 500gb disk only really only has 437.5gb of storage. This is because the advertised size of a disk is to base 10 but the disk size is base 8. Having about 40gb from 395gb used seems about right to me.

---

### Post by roaldz on 2008-02-04
> **marnie6771@gmail.com said:**
> Something strange is happening here: I am converting my cd collection to flac on a 500 Gig internal Hitachi SATA hard disk. For safety I am constantly making backups of my work on an external Lacie 500 Gig hard disk. The Hitachi is formatted in EXT3 and the Lacie is FAT32. Both have an identical directory structure and exactly the same amount of stored data: 395 GB. Only the the LaCie says to have another 100 GB of free space and the Hitachi only 40 GB. Does anybody know why this is? 

Many thanks in advace and kindest regards from

Marcel

Can you connect both drives and run "fdisk -l" and "df -h".
That could clear some things up:)

---

### Post by orange2k on 2008-02-04
FAT32 is not a modern filesystem for todays standards: files larger than 4 GB can not be handled.
EXT3 does not have this problem, and is superior even in comparison to NTFS, because there is little or no fragmentation.

---

### Post by roaldz on 2008-02-04
> **orange2k said:**
> FAT32 is not a modern filesystem for todays standards: files larger than 4 GB can not be handled.
EXT3 does not have this problem, and is superior even in comparison to NTFS, because there is little or no fragmentation.

Ext3 also is a bit more space-efficient. If you really want efficiency, you have to try ReiserFS.

---

### Post by kpkeerthi on 2008-02-04
The advertised 500 GB of space is actually 500000000000 bytes, which equals 500000000000 / (1024 * 1024 * 1024) = ~476 GB. When formatted, the ext3 filesystem does take some space (which grows as more space is being used up) for bookkeeping.

Edit: Added missing zeroes :)

---

### Post by hyper_ch on 2008-02-04
> **kpkeerthi said:**
> The advertised 500 GB of space is actually 500000000 bytes

That's not always true :)

---

### Post by anaconda on 2008-02-04
if you have formatted the ext3 filesystem using ubuntu, then 5% of the space is reserved for user root !!!  (there used to be a reason to reserve 5% of "/" -partition to root, but now I think it is a bug!) The reason was that if the "/" -partition gets full the root user has enough free space to move around and free some space.. ~300MB would be more than enough for that purpose, and it would be needed only in "/" -partition. That ubuntu vastes the 5% even on external drives is a bug..

luckily it can be adjusted afterwards with :
tune2fs -m 0 /dev/sdXX

for more info try "man tune2fs"

---

### Post by marnie6771 on 2008-02-04
Many thanks for your prompt replies!

And kindest regards from

Marcel

---

