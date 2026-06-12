---
title: "Again Partition Mount Issue"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by kauboy on 2008-04-18
I had installed Ubuntu a few weeks back and then decided to format and re-partition one of my inactive (non-OS) partitions using Partition Magic on XP. The new partition works fine with XP, but on Ubuntu 7.10, it doesn't show up on the Desktop like the other partitions which I had before installing Ubuntu. Every time I try to access that newly created partition (NTFS) from Ubu using the My Computer option from Places, it asks me for the Admin password so that it can actually "Mount" it and then it lets me access it. Also, every once in 34 times that I reboot into Ubu, it says "Partition has been mounted 34 times without being checked, checking now..." and runs something like a Disk Check on that partition (sda3). I would like to make this partiton appear on my Desktop, mounted by default, just like the older partitions and am afraid whether that partition will be damaged due to repeated "Checks" and "Mounts". Do help me out. I'm posting this for the second time, I got no help for the first one. :(

---

### Post by joshrobinson on 2008-04-18
post the output of

```
fdisk -l
```

---

### Post by kauboy on 2008-04-18
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaecdaecd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       12880    62500882+   f  W95 Ext'd (LBA)
/dev/sda3           12881       14126    10008495   83  Linux
/dev/sda4           14127       19457    42821257+   7  HPFS/NTFS
/dev/sda5            5100       12748    61440561    7  HPFS/NTFS
/dev/sda6           12749       12873     1004031   82  Linux swap / Solaris
/dev/sda7           12874       12880       56196   83  Linux

---

### Post by joshrobinson on 2008-04-18
hmm, well im alittle confused, because sda3 is a linux partition, not one viewable by windows, so you must be wanting to mount either sda1 sda4 or sda5

with that drive mounted, could you go to
system > administration > system monitor, click the filesystem tab
and take a screenshot of that window?

then below the reply box, click manage attachments, upload the file, and hit submit reply

---

### Post by kauboy on 2008-04-19
I realised my mistake just now. But the problem I specified is correct, except that I'm not sure if its sda3 (Linux - as you rightly pointed out) or sda4 (my new partition in NTFS - as I had mentioned), but its more likely to be sda4, as I have no issues with my Linux partition and its only the new sda4 Storage partition that doesn't mount by itself.
Here's the screenshot you had asked for.

---

### Post by beebelo on 2008-04-19
Have you read this tutorial on FSTAB yet?  
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")
Read this and see if it answers your question.  You should be able to do what you are asking.  It's all in the FSTAB file.

Actrually this one might be better:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by kauboy on 2008-04-19
Oh, and I forgot to mention that it's an empty partition still because I din't want any files on it till this was fixed.

---

### Post by kauboy on 2008-04-19
I can't access that link on FSTAB.

---

### Post by joshrobinson on 2008-04-19
ok here we go

were going to edit your fstab file, this file tells the system what drives to automount, and all the information on them it needs

first we backup your fstab file
```
sudo cp /etc/fstab /etc/fstab.backup
```

```
sudo gedit /etc/fstab
```
add this line at the bottom
```
/dev/sda4 /media/sda4 ntfs-3g rw,defaults,umask=0000 0 0
```
save and close

we are going to mount the drive to /media/sda4 instead of Storage, since its mounted there at the moment

make the /media/sda4 folder
```
sudo mkdir /media/sda4
```

give the system a reboot, and see if it mounts automatically

---

### Post by kauboy on 2008-04-19
Ok, will try and reply.

---

