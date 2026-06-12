---
title: "transferng windows files to ubuntu"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by thespankguy on 2007-10-16
hello all

i currently run xp. i have two hard drives, one which boots windows (40 gb)  and the other is strictly storage (120gb). i want to save all my pictures, documents, mp3s, etc..., switch my hard drives around and run ubuntu from my 120 gb hard drive that currently has no OS on it. 

my main question is how to go about saving all my files (burning is convenient) and getting them back onto my computer once ubuntu is installed. if i burn the "my pictures" folder will it be recognized on ubuntu? does ubuntu recognize .doc files or at least make them .rtf files? i've heard of unrar; will that work with .rar files or do they have to be .tar (or other variations that i've seen)? my main concern is about 6 gb of pictures that i have (.jpgs). i know i could burn them all on the dvd, but they're sorted into folders. would my method work or is there something else i can do?

i'm anxious to get ubuntu istalled!

---

### Post by LowSky on 2007-10-16
short answer: it will work

but why not just create a partition for ubuntu on the 120gb hard drive, and just keep your files where they are now.

---

### Post by bigboy_pdb on 2007-10-16
I found it best to use an external USB hard drive to back up my software and files. I usually burn the documents and programs that are not likely to change (such as my files from when I was in University) to CD-RWs.

If you do make a complete switch, I would recommend changing your external hard drive so that a portion of the external hard drive has an ext3 file system for Linux files and the rest has a FAT32 file system for Windows files. The reason for this is you cannot preserve your Linux file owners, groups, and permissions using FAT32. However, your FAT32 partition on the drive could still be recognized by Windows OSes.

**NOTE:** FAT32 is the file system that most external hard drives initially come with and it is readable by Linux systems and most Windows systems.

---

### Post by rsambuca on 2007-10-16
Ubuntu will work with all those file types.  I strongly urge you to make backups of all your data anyways, especially photos.  The failure rate of hard drives is 8% per year!

---

### Post by thespankguy on 2007-10-16
thanks for the replies. some of that language is cryptic to me and i'll be googling my *** off when i finally go to make the switch. i've already got ubuntu on a laptop that i hadn't been using and i'll be experimenting with how it will recognize anything that i'm questioning. i look forward to being a part of this forum

---

### Post by thespankguy on 2007-10-16
on a side note, why did the word @$$ go to asterisks? that's nuts

---

### Post by rsambuca on 2007-10-16
> **thespankguy said:**
> on a side note, why did the word @$$ go to asterisks? that's nuts

Please read the [forum code of conduct]("http://ubuntuforums.org/index.php?page=policy").  The use of that language is not permitted.  Also, please note that using characters to try and avoid the language filters is also not permitted.  There are users of all ages on these forums.

---

### Post by thespankguy on 2007-10-16
i understand, just wondering if maybe i had a filter turned on by default or something.

---

### Post by sayuki288 on 2007-10-16
try using ntfs-3g

---

