---
title: "Creating a Ubuntu partion with a XP partition on same drive"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by phantomgrave on 2005-12-26
I have a Windows Xp partition on my laptop and im trying to create a new partion with some of the free space on it so i can boot linux or XP when i start my computer. How do i create a partition so i can choose to boot either OS's at start and not lose any data on my xp patition? Thanks in advance.:confused:

---

### Post by jimrz on 2005-12-26
Does your windows partition take up your entire drive and is it NTFS or FAT32?

---

### Post by phantomgrave on 2005-12-26
Yes, it takes up all 30 gigs and its NTFS filesystem, i want to shrink that to leave about 6 gigs for ubuntu.

---

### Post by jimrz on 2005-12-26
The install cd can do that for you, but be sure to backup your data and also defrag your ntfs drive at least 2 or 3 times before you try it. I have seen, on the forums, some intances of problems with this proceedure and others where it worked without problem, so...

   If you have (or can get your hands on) a copy of PartitionMagic, it will handle this task very nicely and without issue from windows. However it needs space to work, and will not go ahead if it does not see enough room to work. If you have 50%+ of your drive free, this would probably be the better option. 

   [**[COLOR="Sienna"]Here[/COLOR]**]("http://users.bigpond.net.au/hermanzone/") is an excellent guide for doing the dual boot install.

---

### Post by phantomgrave on 2005-12-26
thanks, ill try using the one on the ubuntu cd

---

### Post by eriqk on 2005-12-26
I understand Partitionmagic can cause really big and problematic errors.
I did something similar to what you want to do. I used QTparted which I found on a rescue cd (I think it was this: [http://www.sysresccd.org/download.en.php]("http://www.sysresccd.org/download.en.php")) and resized my NTFS partition with it. Looks very much like Partitionmagic, it's free, and it works.
I did defragment my windows partition several times befor doing this, better safe than sorry.

Groet, Erik

---

### Post by phantomgrave on 2005-12-27
thanks, ill take a look at that, i also found this program called swissknife and it seem s like it would do what i was trying to do.

---

### Post by az on 2005-12-27
[QUOTE=phantomgrave]thanks, ill take a look at that, i also found this program called swissknife and it seem s like it would do what i was trying to do.[/QUOTE]

You know, I would think that a great percentage of people who run Ubuntu dual-boot.  Most of the problems with partitioning involve third-party tools.  I think by far, parted and ntfstools (the tools used by the installed and QtParted or GParted) are responsable for the majority of the splitting of partitions with NTFS filesystems.

You will be hard pressed to find posts describing a failed partitioning of an ntfs partition using the Ubuntu installer.   

Ubuntu Forums Statistics

Threads: 112,504, Posts: 625,104, Members: 62,125

---

