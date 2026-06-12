---
title: "Ubuntu shows less free space on partition than I'd expect"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by tokyoTom on 2006-07-12
I hope someone can help me understand this problem which has been counfounding me:

My several-days old installation (Ubuntu 6.06 on an IBM Thinkpad T40) has a 50 GB partition set up to mount as my /home directory.

System>Administration>Disks shows the size of the partition as "49.99 GiB (35.79 GiB Free)." Substraction suggests I have 14.2 GB of data on the partition.

However, right click>properties in the file browser on my /home directory claims 10.7 GB of files. Flielight confirms this 10.7 GB. Both confirm 35.8 GB free-- only adding up to 46.5 GB!

I'm trying to figure out where my 3.5 GB have gone. Any help appreciated.

Bests,
Tom

---

### Post by Kobalt on 2006-07-12
Your 50GB partition is for home only ? That means your installed Ubuntu ( "/" ) on another patition ? Coz the size (3.5GB) match an Ubuntu installation size...

---

### Post by mcduck on 2006-07-12
By default, Ubuntu reserves some space from disks for root only, to make sure that you can't fill your disk so full that you can't boot any more.

I think this defaults to 5% of disk space.

---

### Post by houstonbofh on 2006-07-12
If the first answer didn't help, break into a cli, and play with the commands *mount, df,* and *du.*  A real pain, and not always user friendly, but it will find everything.

---

### Post by tokyoTom on 2006-07-12
Thanks for the advice, all.

My drive has four partitions:
1. Windows (NTFS)
2. Home (ext3)
3. Swap
4. Root (ext3)

To mcduck's suggestion that Ubuntu holds space on the drive, this could make sense if Ubuntu would do this on a /home partition. Would it?

To houstonbofh's suggestion, you make what you describe sound awfully scary, so I may not dig in that direction unless I can find clear instructions on what to look for.

Thanks all. Any ideas on how to get to the bottom of this?

---

