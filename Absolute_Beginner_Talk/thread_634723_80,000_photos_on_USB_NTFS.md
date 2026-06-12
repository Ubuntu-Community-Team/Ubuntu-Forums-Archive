---
title: "80,000 photos on USB NTFS"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by jojopumpkin on 2007-12-08
I have roughly 80,000 photos on a 320GB USB External HD and I'm a little confused regarding NTFS and FAT32. :confused:

I have used this HD on my WindowsXP installation and it reads and writes just as fast as my  internal 80GB but when using it in Ubuntu 7.04 it seems very sluggish.

Would removing the photos and formatting it to FAT32 increase it's read time with Ubuntu? How will that effect it while using it in Windows?



---
I installed Ubuntu simply out of curiosity and it seems the Linux bug got a good bite. I have it installed as a dual boot through Wubi. This is somewhat of an evaluation to see if Ubuntu will stand alone on my HD

---

### Post by mikewhatever on 2007-12-08
The difference between the two file systems are not too hard to find [http://www.google.com/search?hl=ru&client=firefox-a&rls=org.mozilla%3Aru%3Aofficial&hs=nUG&q=ntfs+vs+fat32&btnG=%D0%9F%D0%BE%D0%B8%D1%81%D0%BA&lr=](http://www.google.com/search?hl=ru&client=firefox-a&rls=org.mozilla%3Aru%3Aofficial&hs=nUG&q=ntfs+vs+fat32&btnG=%D0%9F%D0%BE%D0%B8%D1%81%D0%BA&lr=)
FAT32 is an older one, but works out of the box with linux.

---

### Post by Sef on 2007-12-08
GNU/Linux is able to read and write to NTFS files with some software that you need to download for Feisty.  I'll try and find it in a few minutes.   NTFS is better than FAT32.  It is more stable and can handle larger partition sizes than FAT32, which is limited to 4 gigabytes.

---

### Post by Arwen on 2007-12-08
> GNU/Linux is able to read and write to NTFS files with some software that you need to download for Feisty.

It's ntfs-3g,take a look at [here]("http://ubuntuforums.org/showthread.php?t=217009")

> It is more stable and can handle larger partition sizes than FAT32, which is limited to 4 gigabytes.
I didn't quite understand that,did you mean sth different than partition size?Cause I have FAT32 partitions of 30 and 40GB..

---

### Post by Canuckelhead on 2007-12-08
NTFS is better for a lot of reasons...

But even in Win XP I have found my Fat to be faster...  usually not noticeable but I use Fat32 for games.  My understanding is that on fat 32 you have 268,435,445 clusters with 32 kb max per cluster... this yields about 8 terabytes in total on a disk.

my 2 cents

---

### Post by dcstar on 2007-12-08
> **jojopumpkin said:**
> I have roughly 80,000 photos on a 320GB USB External HD and I'm a little confused regarding NTFS and FAT32. :confused:

I have used this HD on my WindowsXP installation and it reads and writes just as fast as my  internal 80GB but when using it in Ubuntu 7.04 it seems very sluggish.
.........

I suspect that Windows will be writing to the external drive in Cached mode wheras Linux is not.

The default Windows method is faster, but runs the risk of data loss if something goes wrong, the Linux method is probably a bit more robust, but (as you experience) slower.

There may be a way to set Linux to uses write caching for an external NTFS drive, but I don't know of it.

---

### Post by jojopumpkin on 2007-12-08
> **Sef said:**
> It is more stable and can handle larger partition sizes than FAT32, which is limited to 4 gigabytes.

I would assume you are referring to the individual file size being transferred to it at one time?

NTFS-3g is already loaded on my system according to my Synaptic. I downloaded the NTFS-3g Config and I will probably reformat the HD using that tool.

Would the fact that I installed Ubuntu through Wubi onto an NTFS drive be responsible for the noticeable decline in r/w speed on my external? Isn't Ubuntu basically running off of a "phoney' ext3 partition?

I was planning on getting Fiesty running solo on this machine anyway, perhaps in doing so I may get some speed back for reading externals.

As always free community support beats call centers ANYDAY! Thank you for the quick replies and resources.

---

