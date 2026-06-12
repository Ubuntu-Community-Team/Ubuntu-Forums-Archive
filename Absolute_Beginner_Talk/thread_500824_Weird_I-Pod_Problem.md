---
title: "Weird I-Pod Problem"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by rookshop on 2007-07-14
I use my I-Pod sometimes to store and transfer data between my laptop and desktop. Today I wanted to do the same. I found that there was not enough space on the I-Pod so I transferred some files to my desktop (Which is Vista BTW). According to Vista there is more than 10 GB of free space on the I-Pod. But when I plug it into my Ubuntu laptop it says that only about 150mb is free. I am left scratching my head as to how this is possible. I dont see the files that I deleted. I ejected and reinserted the I-Pod several times to no avail.

What is the problem?? :(

---

### Post by jpietari on 2007-07-29
I have had weird problems like yours, but with my music library.

**It might be the following:**
1. Files are in a trash can on the drive.  Look for the directory .trash-*user id*.  If it exists, delete the contents

2.  You might have corrupted your music files database on the IPOD.  What I do when this happens is open gtkpod and click File->Create iPod's Directories.  This will delete everything on your iPod and create the iPod directories.  You will then have to copy all your songs over again.

Hopefully this helps.

---

