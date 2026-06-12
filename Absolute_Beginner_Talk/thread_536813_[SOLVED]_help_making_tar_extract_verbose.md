---
title: "[SOLVED] help making tar extract verbose"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-08-28
i have with some mucking round made tar compress some files nicely using this

tar zcvf /media/hdb1/backup/ubuntu-backups/thunderbird/rcc.tar.gz /home/stinger/.mozilla-thunderbird/

how to i take the compressed file i have created and restore them in the "verbose mode" back to thier original place

it will be something simple with the letters after tar, but i dont know what it is...

can you help me please?

---

### Post by stinger30au on 2007-08-28
ah ha! its cool,  you do this

tar &#8211;zxvf

---

### Post by schorsch on 2007-08-28
Per default the tar command strips the leading slash from the path so that it will be untarred with relative paths. Tu use absolute paths you have to modify the tar command to look like this:
```
tar Pzcvf /media/hdb1/backup/ubuntu-backups/thunderbird/rcc.tar.gz /home/stinger/.mozilla-thunderbird/
```
.... or you just change to the directory that you created the tar file from and untar it there while using relative paths.

---

