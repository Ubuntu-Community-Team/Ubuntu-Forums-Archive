---
title: "tar.gz archive corrupt?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-05-31
I have this 6.9Gb archive (I have 64 bit) with lots of important files in it, and I went to extract it because I needed one of the files.  I've noticed that it always gets to the same file, tries for a long time (like 10 minutes) then gives up (at 4.1Gb).  I'm almost certain that there actually is nothing wring with the archive because 
I checked  it right after the initial compression/creation of it.  What should I do to get the files out!?

Luckily, the bulk of the files in it, at least most of the important ones, were extracted successfully, I think, but how can I be sure, and what about the rest![-o<:x:(

---

### Post by yabbadabbadont on 2007-05-31
Make sure that your gunzip, gzip, and zcat programs can handle large files.  Tar (I think) is piping the file through one of them before extracting.  You might see if you can gunzip the file so that you just end up with a plain *.tar file.  It is very easy to recover files from one of those as tar just adds some headers and padding to each file that is stored.  (I wrote a DOS tar program a *very* long time ago ;))

---

### Post by ryanVickers on 2007-05-31
Wow, mabey ther's hope yet! :)
That was what it was complaining about, something about bad commpression headers, or unvalid something...

> You might see if you can gunzip the file so that you just end up with a plain *.tar file. It is very easy to recover files from one of those as tar just adds some headers and padding to each file that is stored. (I wrote a DOS tar program a very long time ago )
How would I do that exactly?

---

### Post by yabbadabbadont on 2007-05-31
Assuming that you have a partition with enough free space to hold the uncompressed file...  ;)

Open a terminal window and run ```
zcat archivefile.tar.gz > /path/to/partition/with/freespace/archivefile.tar
```
If you don't get any errors, then you can try to extract the rest of your files from the uncompressed tar file you just created.

---

### Post by ryanVickers on 2007-05-31
It seemed to work, but there was the commandline output:
> tar: Skipping to next header
tar: Error exit delayed from previous errors

And I could tell it was still missing files/stuck at the same point as before.

Any more ideas? :(

---

