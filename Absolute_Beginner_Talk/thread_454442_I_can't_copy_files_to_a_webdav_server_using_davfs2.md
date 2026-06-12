---
title: "I can't copy files to a webdav server using davfs2"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Biochem on 2007-05-25
I mounted my webdav account using this command:

sudo mount -t davfs -o uid=Biochem,rw,dir_mode=775,file_mode=775 [https://www.server.ca/dir/](https://www.server.ca/dir/) media/Maison

I can creat file and folder but when I try to copy some file by entering:

cp -r /media/Microscopy/Sam /media/Maison

I get I the following error message:

cp: cannot create regular file `/media/Maison/Sam/D5_GFP_02.tif': Invalid argument

I also have the same invalid argument when I use tar.

Any Idea what I'm doing wrong?

Thanx

---

### Post by Biochem on 2007-05-30
bump

---

### Post by Biochem on 2007-06-08
I don't like to do this but
bump

---

### Post by ubuntulnx on 2007-11-15
i had the same problem on debian etch. change use_locks value to 0 in the config file.

worked for me.

---

