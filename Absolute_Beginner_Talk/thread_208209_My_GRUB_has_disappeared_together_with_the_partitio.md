---
title: "My GRUB has disappeared together with the partitionI deleted"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by ChiendeRue on 2006-07-03
Ahem, beginner's hubris:

_This used to be my computer set up:_ (the good old days when all was working)

Physical Disk 1:
1 partition (NTFS) of 143 GB containing Win XP

Physical Disk 2:
1 partition (NTFS) of 120 GB containing 73 GigaByte of Mp3's
3 partitions: the three partitions containing Ubuntu (root, home, swap) = the other 23 GB of that physical disk

_What was I thinking?_

I was unhappy with the fact that ubuntu couldn't write on my 120 GB NTFS, only read
I knew that FAT 32 doesn't solve my problem since max size is 32 GB
I knew that HFS+ Apple would allow me to have a 120GB that is read AND write

_What was my frustration?_

Windows didn't allow me to reformat the NTFS (120 GB) to HFS+ (even if I have MacDrive 6 installed -that one would not allow me to format THAT disk)
I didn't know how to do it from Ubuntu (If it is at all possible)

_So how did this genius mess up?_

I deleted the 120 GB partition from Windows XP (even if I had to force that deletion - I know, I know...)
After that it was sayonara to my boot-up

_Then what did I try?_

I fixed the MBR with my Win XP install disk. Success! I'm typing in windows now.
I downloaded Ubuntu alternate disk (couldn't fix it)
I downloaded Ubuntu supergrub disk and tried to repair grub (no success)

_So what now?_

I used Ubuntu live CD, hoping to recover files from home folder but I can not read any of the linux disks: "can not mount the volume"
I thought of reinstalling Ubuntu but will I be able to read volumes then?

**_Does anyone know the easy way out?_**

---

### Post by lamego on 2006-07-03
> I knew that FAT 32 doesn't solve my problem since max size is 32 GB - This information is not correct, FAT32 does support 120 GB. However the windows format does not support it, you will need to format it with some other utility.
You should be able to access to your linux partitions from the Live CD, from a terminal try listing the partitions with:
```
sudo fdisk -l
```

Installing ubuntu will not change the ability to recover the files.

---

### Post by ChiendeRue on 2006-07-03
I executed the command in a terminal
screenshot-1
Next thing I still can't mount the volume
screenshot
I am truly a beginner, sorry. If a reckless one, I know...

---

