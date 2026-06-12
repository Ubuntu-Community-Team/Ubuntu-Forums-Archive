---
title: "Indexing slowing down system"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by mikajake on 2007-06-04
I am relatively new to Ubuntu and I can't for the life of me figure out how to search for files based on their extension.  I thought it was because I had not indexed the system.  So I started that and now my system has slowed down to almost a standstill.  So two questions, the first as stated above about searching for files by extension, and the second, can I turn off the indexing get my speed back up to snuff.  Does this indexing take some time to complete?

Thanks
Mikajake

---

### Post by DBStevens on 2007-06-04
You can use the find command for example

find / | grep "\.conf"

will produce a list of all files containing  .conf in the file name.

You will also get permission warnings when find enters a directory that you as a user aren't supposed to be able to read.

Note this really isn't a true extension just that file name contains .conf in its name.

If by indexing you mean building the locate data base, yes that can be turned off, it is normally a cron scheduled run.     

Locate allows one to find things by using the locate command for example:

locate *.conf 

would produce a list of all files ending in .conf .

The locatedb indexing is controlled by the slocate shell script in /etc/cron.daily

If by indexing you mean some system other than locate please let me know.

The indexing time depends on the number of files on your file system and other factors.

---

