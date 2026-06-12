---
title: "Re: Deleted Wrong Partition"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Greevous on 2007-12-27
To borrow Mattevt's words... [I screwed up really really bad]("http://ubuntuforums.org/showthread.php?p=4012635#post4012635").

I accidentally deleted a partition on my external drive with gparted. The filesystem was ext3, the size was roughly 150GB, and 30GB was being used for files.

What happened was I deleted the partition and applied the changes in gparted, THEN realized that I had been working with the wrong drive. Since it was ext3, I only deleted the partition once, and I haven't written anything to the drive since then, I was really enthusiastic about being able to restore my lost data.

I used **gpart** to try to guess the partition. After that, I would use that information to recreate the partition table and hopefully get my data back. Unfortunately, this is what gpart found:
```
Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
```

Any suggestions or data recovery techniques?

---

### Post by Sef on 2007-12-27
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by Jimmey on 2007-12-27
**testdisk**

Try
```
sudo apt-get install testdisk
```

and then 

```
sudo testdisk
``` 

In a terminal.

Note that Testdisk can be used to recover deleted partitions. If this doesn't work, you can always scan the disk for files using photorec, like so:

```
sudo photorec
```

The interface takes some getting used to, but the filesystem wasn't congested, and as long as you've not written anything to the disk since, then most of the files will still be there. Good luck!

---

### Post by Greevous on 2007-12-27
I am using testdisk, but when it asks for the partition table type, does it mean the type that it is currently using now? If that's the case, then it's non partitioned media (since I deleted the partition). If it is referring to the state that it was in before I erased it, then I would guess intel?

Edit> TestDisk says,
> Note: Do NOT select 'None' for media with only a single partition.[B] It's very
rare for a drive to be 'Non-partitioned[/B]'.

However, at this point in time my drive *is* unpartitioned.

And should my drive be mounted before I proceed with testdisk?

---

### Post by handaxe on 2007-12-27
The partition type refers to the working condition of the drive, so choose a partition type.

The disk can be mounted AFAIK.

HA

---

### Post by Greevous on 2007-12-27
Sorry- "working" as in current? Or "working" as in when I was last able to access my data?

The drive is currently non-partitioned, but that note that TestDisk gives worries me a little, because what I'm trying to recover *is* a single partition.

---

### Post by handaxe on 2007-12-27
Working as in what you "lost".

Testdisk is going to rewrite the whole partition table to do its stuff so in a sense the table is what you are recovering, not the partition per se.

As far as I recall, testdisk is pretty harmless up until you choose to save the partition table so go ahead and run the scan and see what it finds (but read everything you can find first).

And Intel /PC it most likely is unl;ess you have a MAc etc.

HA

---

### Post by Greevous on 2007-12-27
I have my data back now. :-D

I took a chance and chose "Intel/PC" as the partition table type, assuming that it wanted the type of partition that I was trying to **recover**, not the type that I had possession of. (Now I know that was the right choice after handaxe posted.)

I continued through TestDisk's prompts, it located the exact partition that I lost, then I wrote the changes and everything was back to normal.

---

### Post by Rui Pais on 2008-01-11
> **Sef said:**
> Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

Thanks a lot.

Yesterday i needed to install an old copy of W2K on my file server, and the creature changed the order of drives, one of them SATA and not manageable by WIndows installer...

Needless to say that installation seemed to take forever just to abort and leave me to an unbootable HD with just a single "unallocatable space" on it, and ALL my files, backups, works from university, etc... completely lost. I almost fall round in the ground.

A quick search give this thread. I didn't know that amazing application!!!
Now all my partitions are back again, i only lost an old Feisty install that i have on 1st partition of that disk, incorrectly  overwitten by Windows. All rest came alive with the partition table restore :) :)

I'm so happy and greatful for this :D!!!
Thanks.

---

### Post by pereclies on 2008-01-12
> **Sef said:**
> Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

OMG I have my data back!! Thank you for telling me to use TestDisk:guitar:

---

