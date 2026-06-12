---
title: "tar and gz"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by measekite on 2007-09-21
I see compress files with this type of filename.

filename.tar.gz

What does the tar mean?

What does the gz mean?

Why do they have 2 extensions?

---

### Post by LaRoza on 2007-09-21
tar = Tape Archive
gz = GZip

Together, this is called a "tarball".

It is a way of grouping files and folders, and compressing them. The extension don't mean anything, they are for the user.

```

tar -zxvpf my_tar_file.tar.gz

```


-z - unzip the file first 
-x - extract the files from the tarball 
-v - "verbose" (i.e tar tells you what files it's extracting) 
-p - preserves dates, permissions of the original files 
-f - use the file in question (if you don't specify this, tar just sort of sits around doing nothing)


For more:

[http://www.linux.org/lessons/beginner/l15/lesson15b.html](http://www.linux.org/lessons/beginner/l15/lesson15b.html)

---

### Post by insane_alien on 2007-09-21
tar means it is a tape archive. but nobody (outside backups)uses tapes anymore so now it just means it's a bunch of files stored in a single file.

the gz means it is compressed using gzip i think. 

extensions don't matter in linux you could call it filename.jpg and linux would still pick it up as a .tat.gz since it uses MIME types.

---

### Post by Pumalite on 2007-09-21
'tarball'

[http://en.wikipedia.org/wiki/Tar_(file_format](http://en.wikipedia.org/wiki/Tar_(file_format))

---

