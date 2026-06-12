---
title: "Setting up my HD partitions"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by matthewkris on 2007-09-06
Hello all,

Need some advice on setting up my partitions before I move forward.  I have an 80 gig drive with 60 of it already allocated to my XP install.

So right now I am sitting with 10 gigs unallocated and need to know how I should set it up.  I've seen a million different articles and suggestions.  Do I just need a EXT3 partition and a small SWAP partition?  Some people recommend a seperate one for USERS but others do not.  I am basically just going to be playing with Ubuntu so nothing serious, I will be the only user and I am not concerned with sharing files between XP and Ubuntu.

Please suggest before I screw something up. Thanks in advance.

---

### Post by BobCFC on 2007-09-06
The default install is as you say, one big Ext3 partition for both programs and user data, and a smaller separate swapdisk.

The /home dir is akin to the MyDocuments folders on windows but it is used more often.. almost everything is saved there; all your program settings, downloads and bookmarks etc

The reason some people like to have a seperate /home drive is that if it runs out of space it wont affect the system files and it is easy to move the /home folder to a new drive and carry on without breaking any programs.

You can still move the home folders to a separate partition afterwards if you initially choose one big drive but it is a little more work.

If you are just experimenting then you will be fine with one big drive but be careful if you save gigs and gigs of downloads to your home folder.

---

