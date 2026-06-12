---
title: "[SOLVED] Partimage &amp;quot;out of space&amp;quot; message"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by dansan on 2008-04-18
I'm new to Ubuntu and having a problem with Partimage. I want to use it to back up my system/apps partition.

I've been booting from SysResCD. The hardware is a PC with 2 external SATA HDs connected via USB. One of these has UbuStudio set up on two partitions for the system and apps (5GB) and data (20GB).

The other external HD has an ext3 partition (27GB), which is where I want to store a backup image of the 5GB Ubuntu partition. You'd think I'd have enough space, but  Partimage keeps stopping the copy because of insufficient space.

Partimage 1 shows what Partimage reports about the partitions. Following the how-to on using Partimage at  [http://www.ubuntuforums.org/showthread.php?t=287522]("http://www.ubuntuforums.org/showthread.php?t=287522"),  I entered "mkdir /backup" and "mount /dev/sdd3 /backup". After starting Partimage I selected sdb6 as "Partition to save/restore" and followed each step thereafter until Partimage reported that the copy would need 3GB.

Partimage started the copy, but, as mentioned, stopped because "The disk is full." How can 3GB fill a 28GB partition? I think I've misunderstood the directions. Can someone please point out where?

TIA.

Daniel

---

### Post by dansan on 2008-04-18
](*,)

I always try to read carefully, but often I fail when tired. Under step 2.1 in the how-to I failed to see /backup/... , so I just put in a filename. Those li'l characters were the key, and after I typed 'em in everything worked as it should.

As my math teacher used to say QED, which he claimed meant quite easily done.

Daniel

---

