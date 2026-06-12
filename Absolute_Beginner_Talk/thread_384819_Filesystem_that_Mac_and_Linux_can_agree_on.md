---
title: "Filesystem that Mac and Linux can agree on?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by arthurbarnhouse on 2007-03-14
I'm reformatting my hard drive so that it's not hfs+ anymore, so that I can read and write.  However, I want to be able to switch between a linux machine and a mac.  which filesystem is optimal for this sort of setup?

---

### Post by eljalill on 2007-03-15
Well, if it is a third partitions (neither Ubuntu system partition, not Mac system partition), or an external hard drive, ext3 should work... google tells me, there are ext3 drivers for Mac. 

I have not tried it out though. 
Maybe someone else has?

I don't think this works however for a Mac system partition.

Best of luck.

---

### Post by kambei on 2007-03-15
FAT32 is read/write usable by both Linux and a Mac... fine for storing user files (pics, music, movies, etc.) but perhaps problematic for programs...

---

### Post by AtrejuT on 2007-03-15
I'd guess Fat32 should work as well - though its not the most modern FS anymore...

---

### Post by arthurbarnhouse on 2007-03-15
Yeah, I thought about FAT32, but isn't it limited to 32GB partitions?  my external is 160GB.

---

### Post by jincast90 on 2007-03-15
> **arthurbarnhouse said:**
> Yeah, I thought about FAT32, but isn't it limited to 32GB partitions?  my external is 160GB.

Nope it isn't my external harddrive is over 32gb, and it has a FAT32 partition. You can although only write files up to 4gb large on your harddrive if you use FAT32.

---

### Post by kambei on 2007-03-15
> **arthurbarnhouse said:**
> Yeah, I thought about FAT32, but isn't it limited to 32GB partitions?  my external is 160GB.

fdisk in Windows is limited to the size of FAT32 it can *create*... but you can use the Linux fdisk to make a 160GB FAT32 that is usable both in Linux and Windows.

One thing to consider, though, is I think you are limited in the size a single file to a max. 4GB on FAT32...?

---

### Post by arthurbarnhouse on 2007-03-15
I don't have any files over 2.3 Gigs, according to Disk Inventory, so I should be fine on that front.  Is it dangerous to have a formatting above 32 Gigs?  Why does the window's Fdisk limit it but not linux?

---

### Post by kambei on 2007-03-15
Microsoft limited (crippled?) fdisk's capability to write larger FAT32 partitions to encourage - I believe - the adoption of NTFS.

Beyond the inherent limitations of FAT32 itself, I don't think there are any problems in using large FAT32 partitions.

---

### Post by kambei on 2007-03-15
One area where the 4GB file size limit on FAT32 might bite you is DVD image files...

---

### Post by kidders on 2007-03-15
Hi there,

Personally, I always use HFS+ on devices I'm sharing between OSX and Linux. The lack of a filesystem journal is irritating, but not as irritating as FAT32!!

---

### Post by arthurbarnhouse on 2007-03-15
But you can't write with HFS+, and without that the hard drive is next to useless for what I want to set up.  FAT32, will work fine.  Thanks, all.

---

### Post by kidders on 2007-03-15
> **arthurbarnhouse said:**
> But you can't write with HFS+, and without that the hard drive is next to useless for what I want to set up.Writing to HFS+ is no problem. All you need to do is switch off its journal.

---

### Post by keheikev on 2007-03-15
or long podcasts when you jump into video or video editing.
kiheikev
:popcorn:

---

