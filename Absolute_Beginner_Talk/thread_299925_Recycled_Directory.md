---
title: "Recycled Directory?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-11-14
I read somewhere, but can't find it now, that under certain circumstances when a file is deleted, Linux creates in a root directory a folder called "Recycled."  Could anyone please point me to information about that?  Thanks in advance.

Buck

---

### Post by Arndt on 2006-11-15
> **Buck2348 said:**
> I read somewhere, but can't find it now, that under certain circumstances when a file is deleted, Linux creates in a root directory a folder called "Recycled."  Could anyone please point me to information about that?  Thanks in advance.

Buck

I haven't heard of a directory called "Recycled", but it reminds me a little of the lost+found directory at the top of each partition, into which files are moved by the file system recovery program 'fsck' if it find files which lost their connection to the directory they were in.
For some reason, "man fsck" doesn't mention "lost+found".

---

### Post by bodhi.zazen on 2006-11-15
Linux will create a similar type of directory in your home directory called .Trash

.Trash is hidden

There will also be one in /root/.Trash

Deleted files will be placed here.

See here: [Trash](http://www.ubuntuforums.org/showpost.php?p=1514142&postcount=6)

for other WM: [alternate trash](http://www.ubuntuforums.org/showpost.php?p=1235410&postcount=8)

---

