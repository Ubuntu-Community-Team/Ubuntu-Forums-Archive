---
title: "A little help needed...."
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2005-12-12
Right, i`m currently running Ubuntu Breezy...its the best thing ever. Recently i was inspired to remove all connections with windows (havent used it in months but still had a broken copy of it[actually i  think they`re all broken]) now then....i`m feeling somewhat adventurous but i need a little help in sorting out my partitions beforehand.
  Breezy is installed on its own hard drive so thats no problem, however i have a rather large amount of music 'backed up' on my other 123gb hd which used to contain windows. the linux hd is only 40gb so i cant take the easy route and copy my music over to it while i wipe the 123gb hd clean. What i want to do is, set up a new partiton containing my music on the 123gb (around 50gb perhaps), then using the rest of it, install a new OS, i dunno which one yet, maybe another linux distro or try out Amiga software, i`ve not decided, but if someone could help me out sorting out this partitioning malarky i`d be very appreciative.

if this makes no sense please ask me to clarify

---

### Post by matthewv on 2005-12-12
Download and install gparted on ubuntu. Use this to resize the windows partition to quite small, and then create a new ext3 partition in the free space. Copy your music to this partition, then erase the other partition and create a new ext3 in its place. Format the new partition, copy your music back, delete the old backup partition, and resize your other partition so that it fills all available space. If you need further help (or dont understand this) just post here.

---

### Post by aysiu on 2005-12-12
So your music is on a 123 GB hard drive but uses up only 50 GB of space? Maybe you should consider some kind of compression/backup utility that could save the 50 GB of music as some kind of .gz that can be unpacked again after you reformat the drive.

I'm no expert on this, but I'm pretty sure it can be done.

**Edit**: Actually, matthewv's suggestion is even better!

---

### Post by DiscoKiller on 2005-12-12
i have gparted installed, however, when i select the 'windows' partition, i cannot edit it at all. theres a little padlock emblem next to it.  i tried using the terminal and typing sudo gparted to run it as root but the same happened, 

oh yeah, the partition i want to edit is presently fat32 just incase you were wondering

---

### Post by matthewv on 2005-12-12
You need to unmount if first probably. Right click on the partition and press unmount.

---

### Post by DiscoKiller on 2005-12-12
Thank you sir, currently resizing. You`ve been a great help. I knew what i wanted to do but i didnt think it was worth doing it without a bit of help. Again thank you.

DK

---

### Post by DiscoKiller on 2005-12-12
OK, Partitions have been created. I have re mounted the original partition with my music etc on it, but i have no idea how to mount the new partition.

tried editing fstab but i dont really know what i`m doing.

the partition is ext3 on /dev/hda2

---

### Post by DiscoKiller on 2005-12-12
Discontinued Thread....i Sorted It :)

---

