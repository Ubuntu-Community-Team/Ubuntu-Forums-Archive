---
title: "Will this mess up my Windows partition?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by fiel on 2008-01-05
Hi everybody,

I have Ubuntu installed in a a 10 GB partition and Windows XP all in 60GB.  If I keep all of my Word Documents and MP3's in  my Windows partition will anything bad happen if I access this partition from my Ubuntu partition when working on Word files or listening to music?

Thanks.

---

### Post by mdpalow on 2008-01-05
Obviously these files are important to you, so why not make a back-up first? :)

Then IF something happens it won't really matter.

I've accessed files/movies/music in a Windows partition and nothing happened. Make sure Open Office is set to save Word documents as '.doc'.

Good luck...

---

### Post by adam.tropics on 2008-01-05
The ntfs support is 'fairly' solid, but as stated it wouldn't hurt to make sure you are properly backed up first. (If for no other reason than to avoid having to read a thread title like 'Ubuntu killed my Documents'!!!)

---

### Post by Rocket2DMn on 2008-01-05
ntfs-3g provides solid support for reading/writing ntfs partitions (which is what windows uses), so you will need to install that and enable write support first.  Of course, you should always keep good backups of your data, regardless of what type of drive you are using.
I play my music and access plenty of files from my windows partition without any trouble.

---

### Post by mdpalow on 2008-01-07
ntfs-3g comes installed with Ubuntu 7.10, so you shouldn't even have to install it.

---

