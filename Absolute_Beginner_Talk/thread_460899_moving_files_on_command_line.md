---
title: "moving files on command line"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by jonyboy1000 on 2007-06-01
Hi all.

I've been using Linux for a while now and want to use the command line much more than i do currently.

I have a set of folders (inside one folder) and would like to bring all my images from my subfolders into my main folder so that

./xyz/Europe/2007-europe-001.jpg
./xyz/Europe/2007-europe-002.jpg
./xyz/Europe/2007-europe-003.jpg

and 

./xyz/Cyprus/2005-crprus-001.jpg
./xyz/Cyprus/2005-crprus-002.jpg
./xyz/Cyprus/2005-crprus-003.jpg

just become 

./xyz/2007-europe-001.jpg
./xyz/2007-europe-002.jpg
./xyz/2005-crprus-001.jpg
./xyz/2005-crprus-002.jpg

(this would be from 20 folders with 100 pics in each)

---

### Post by gerscht on 2007-06-01
This should do (make a directory outside the directory to be searched first):
```

mkdir /home/NAME/whatever;
find /xyz/Europe/ -name \*.jpg -exec mv {} /home/NAME/whatever\;

```

Now you'll have all files in /home/NAME/whatever

---

### Post by jonyboy1000 on 2007-06-01
I found out how to do it! Thanks

I made a new folder and remembered to use a wild card (because of your post)

so i just did

> mv ./europe/2007-europe-* ./whatever

---

### Post by gerscht on 2007-06-01
```
mv ./europe/2007-europe-* ./whatever
```
That works as well, of course.
using the find syntax will get the files recursively, so you don't need to go into each folder. But I suppose, 20 folders are not that many ;)

---

