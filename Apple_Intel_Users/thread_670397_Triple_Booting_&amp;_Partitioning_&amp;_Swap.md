---
title: "Triple Booting &amp; Partitioning &amp; Swap"
date: 2008-01-17
forum: Apple Intel Users
---

### Post by petersrin on 2008-01-17
OS X and Ubuntu installed fine. Details:

Partitions:

"Mac OS X" : 200 GB
"Linux" : 10 GB
"Swap" : 1 GB
"EFI" : 200 MB
Free Space : 20(ish)GB

I want to make free into XP, BUT of course, only 4 partitions per drive are legal... and most "modern systems don't even use more than 10MB of swap." If that is the case, I'd like to remove the Swap partition, replace it with a 200MB swap file within the Linux partition, then install XP on the 20GB free space. I found a solution on a Red Hat forum, but the location of the swap definitions in the Linux part seem to be different in ubuntu, so I can't "swapoff /dev/hdb2" as suggested. Ideas? Thanks.

---

### Post by cyberdork33 on 2008-01-17
> **petersrin said:**
> 4 partitions per drive are legal... 
Not exactly, but for Windows, yes.
> **petersrin said:**
> and most "modern systems don't even use more than 10MB of swap." 
I don't know about that... to hibernate, you need AT LEAST as much swap as you have of RAM to make sure that it can save the contents of the RAM before powering down.

> **petersrin said:**
> If that is the case, I'd like to remove the Swap partition, replace it with a 200MB swap file within the Linux partition, then install XP on the 20GB free space. I found a solution on a Red Hat forum, but the location of the swap definitions in the Linux part seem to be different in ubuntu, so I can't "swapoff /dev/hdb2" as suggested. Ideas? Thanks.
just remove the swap line from your /etc/fstab. Then you can reboot into a live cd and do what ever changes you need. Note that you will likely mess up the entries in /etc/fstab if you move partitions around.

---

### Post by petersrin on 2008-01-17
Thanks. I didn't know where those config files were. That did it, actually.

---

### Post by petersrin on 2008-01-17
Actually, not quite true. Opening qtparted, I noticed that I now have 3 seperate free space sections. Of course, Windows thinks that are all partitions. So I need to move the three of them into 1 larger free section... but qtparted won't let me do any functions to freespace. Any ideas?

---

### Post by cyberdork33 on 2008-01-17
> **petersrin said:**
> Actually, not quite true. Opening qtparted, I noticed that I now have 3 seperate free space sections. Of course, Windows thinks that are all partitions. So I need to move the three of them into 1 larger free section... but qtparted won't let me do any functions to freespace. Any ideas?The Mac likes to leave spaces between partitions for some reason.

move/resize the other partitions if you can.

---

### Post by petersrin on 2008-01-17
qtparted partition table:

```
Free - 0MB
fat32 - 200MB (EFI)
hfs+ - 200GB (Mac OS X)
free - 22.71GB (to be XP :(  )
ext3 - 9.98GB (Ubuntu)
free - .59MB 
```

I'm in a live boot of Knoppix running qtparted. The EFI allows resizing, but it can't actually resize anywhere since the one before is essentially nonexistant anyway.
The Mac OS X and Ubuntu don't allow anything except for format, which I'm not doing, for obvious reasons. So, I've got a bit of "free" space at the beginning and end, totaling .59MB that are looking to windows like extra partitions, but I can't seem to get rid of. I tried a

```
umount /dev/sda4
sudo qtparted
```

to see if it was possible to unmount the drive, then drop to root and access those options. That's a no-go. Thanks.

---

### Post by cyberdork33 on 2008-01-17
Do not mess with the EFI partition.

I don't understand what you are trying to do now. If you are creating a new partition you are going to have to format it eventually (not the entire drive, just the partition).

can you give the output of the GPT partition table:
```
sudo parted /dev/sda print
```and the MBR table:
```
sudo fdisk -l /dev/sda
```

---

### Post by petersrin on 2008-01-17
Ok. Here it is. I am trying to install XP as my third OS.

The install CD will not create a partition when there are already 4 partitions. Each of the free spaces seem to be viewed as partitions by that CD. If I could eliminate them, then I'd be able to create the ntfs partition...

But qtparted won't let me get rid of the first and last free space parts.

---

### Post by cyberdork33 on 2008-01-17
yea but you are not showing your partition info well enough so I can see what is really there...

```
sudo parted /dev/sda print 
```

```
sudo fdisk -l /dev/sda
```

---

