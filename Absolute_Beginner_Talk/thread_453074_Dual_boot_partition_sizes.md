---
title: "Dual boot partition sizes"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by dunklegend on 2007-05-24
I've done several successful dual boot installations and I had something like this:

Windows XP|Ubuntu|Swap File|NTFS

The hard drive I'll be using for this is a 250GB one.

My questions are:

1.- How do I have to partition my disk so I have something like this:

      Windows XP|Ubuntu|Swap File|Home|NTFS
      (I think that I can only have 4 primary partitions and after that they have to be extended, but I don't know                                                           how to do it.)
       I want to create the home partition so I can save my settings.

2.- What sizes are a good fit for this hard drive.

---

### Post by mikewhatever on 2007-05-24
Home partitions sizes can range from 10 to 250 GB, whatever is convenient. It is more important to allocate about 5 BG to the root.
Once you create an extended partition, you can create many (256) logical ones within it. There is an option in Ubuntu partition manager to create an extended partition by clicking on unallocated space.

---

### Post by dunklegend on 2007-05-24
OK so I need to create an extended partition.

What should I assign to this extended partition?
Ubuntu?, swap file?, home file? or NTFS?

If you had this hard drive how would you partition it?

Order of partitions, type of partitions (primary, extended), size of partitions.

Thanks in advance

---

### Post by dumbledore on 2007-05-24
Hi,
You can use Gparted or Partition Magic (in Windows) by resizing the biggest partition you have (may your ntfs), and then you copy all you data in /home to new partition and then change your /etc/fstab.
Make sure the mount point /home point to the new partition.

ATTENTION: Make BackUp for your data first!

:)

---

### Post by dunklegend on 2007-05-24
Right now I don't have any data that I need to save.
I rather start with a fresh disk and create partition sizes that are going to be enough in the future.

My other problem is that I don't know which partition/s should be in the extended partition.

If anyone has a configuration like mine or knows how to do it please let me know:
Order of partitions, type of partitions (primary, extended), size of partitions.

The only thing I know for sure is that the windows partition has to be the first one.

Thanks

---

### Post by mikewhatever on 2007-05-24
As I said earlier, the extended partition would hold the logical ones, which can be all but XP system, or all Ubuntu related. For example, here is my disk setup
> /dev/sda1   *          63    58878224    29439081    7  HPFS/NTFS
/dev/sda2       137869830   154191869     8161020    c  W95 FAT32 (LBA)
/dev/sda3       154191870   156296384     1052257+  d7  Unknown
/dev/sda4        58878225   137869829    39495802+   5  Extended
/dev/sda5        58878288    97948304    19535008+  83  Linux
/dev/sda6        97948368    98944334      497983+  82  Linux swap / Solaris
/dev/sda7        98944398   137869829    19462716    b  W95 FAT32

sda1, sda2,sda3 are primary, sda4 is extended that contains root swap and FAT32.

If I had you disk,
Windows 50 GB
Extended partition 200 GB
  Ubuntu root 10 GB
  Swap 1-1.5 BG
  Home 50-100 GB
  NTFS the rest.

---

### Post by dunklegend on 2007-05-27
Do you think the ubuntu root partition is OK with 10GB?
What's the biggest root partition you've seen?

---

### Post by rusty4r on 2007-05-27
I agree with mikewhatever

---

