---
title: "HELP!!! I just bought a harddrive but I don't know how to format!"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2006-06-24
I just bought a harddrive and an enclosure connecting to my laptop!

I am using QParted right now.
It asks me whether I want to create a primary or extended partition.

What should I use?

---

### Post by raptros-v76 on 2006-06-24
primary partition. extended partitions are partitions within partitions

---

### Post by boom2k1 on 2006-06-24
what is the difference??

I am going to use it as a storage device!

Thanks!

---

### Post by raptros-v76 on 2006-06-24
you cant make an extended partition outside of a primary partition. also make sure you are making the primary partition on the new hardrive, (dont wipe the one with your linux on it.) just trust me, you want a primary partition

---

### Post by boom2k1 on 2006-06-24
I will use this harddrive by breaking them into several partitions.
Like 5 or something, all for data backup and storage.

Some might be in FAT32, some in EXT3.. etc

Thanks!

---

### Post by boom2k1 on 2006-06-24
Thanks!!

One quick question. Fat32 or Ext3
I also need to boot to Windows XP at times to work on other stuff.

What is the advantage of Ext3 for storage anyway?

Thanks!

---

### Post by raptros-v76 on 2006-06-24
why? you lose space for the partition boundaries. also, if its an IDE disk, then you can only make 4 primary partitons.

---

### Post by BatteryCell on 2006-07-27
In case you were still wondering I think that ext3 is faster.

---

### Post by Lord Illidan on 2006-07-27
Ext3 may be faster and have journaling and stuff, but it's not compatible with windows xp..(well, unless you install the right drivers)

Fat is the way to go for external drives so far.

---

### Post by NeoGreen on 2006-07-27
Sorry, to ask a question on your thread, but what is the difference between FAT, FAT32 and NTFS.  Does Linux use those types of partitions?  :confused:

---

### Post by Brunellus on 2006-07-27
a short history/discussion of the FAT filesystem:

[http://en.wikipedia.org/wiki/FAT_filesystem](http://en.wikipedia.org/wiki/FAT_filesystem)

NTFS:

[http://en.wikipedia.org/wiki/Ntfs](http://en.wikipedia.org/wiki/Ntfs)

In general:

FAT32 is well-understood and will deal with files up to 4GB in size.  Linux can read and write to it with no problems, as can Windows.   Downside:  fragmentation (not a problem with ext3 and reiserfs), no support for filesystem-level permissions and that 4GB limit on filesize.

NTFS is Windows' new filesystem.  It doesn't fragment as much as FAT32 (still fragments enough to need regular massaging, though).  No 4GB limit on individual filesize.  Linux cannot write to it safely yet.  Writing to NTFS partitions with Linux can cause irrecoverable filesystem corruption.  You have been warned.

So for any removable media that you want to guarantee cross-platform compatitibility, go with FAT32, provided you don't need files bigger than about 4GB each.  Beyond that, you're in *nix territory:  XFS, ext3, Reiser3 and Reiser4, and so forth.

---

### Post by BatteryCell on 2006-07-27
Hmm speaking of which this thread just reminded me that I had a 30 gig hd i had meant to install..lol its unformatted so I plugged it in and booted to linux where I ran qtparted and it saw the hd.  My question (seeing as ive never used qtparted before) is how do I actually make it format the disk, when I select the partion on the disk that is the 30 gig one that doesnt have a filesystem and say format, it asks me for a name and what type so i gave it one and told it to format to ext3, then as soon as i pressed ok it showed that it had been formated, instantaneously, arent you supposed to see it formating or something?? And why, when i click on sda (the main one) and then go back to hdb (the new one) does it lose its formatting?

---

### Post by BatteryCell on 2006-07-27
ah ha u have to commit... lol like the phrasing :-D

---

### Post by NeoGreen on 2006-07-27
Thanks for the inforation.  I didn't realize there was a difference between FAT and NTFS.  :D

---

