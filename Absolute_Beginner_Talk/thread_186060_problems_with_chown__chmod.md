---
title: "problems with chown / chmod"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by aleskm on 2006-06-01
Hi,

chown and chmod commands don't work for me. 

for example I want to make a link to midnight commander. I use command

sudo ln -s /usr/bin/mc /home/ales/Desktop/mc

which created link. But I cant use it because this file is now owned by root. I want to change ownership, so I write

sudo chmod ales:ales /home/ales/Desktop/mc

and owner of the file is still the root.

what do I do wrong ? :confused: 

I've got similar problems with chmod, even when I want to e.g. assign a right to write for group for a file which I created (and is owned by me), Linux says that "The permissions could not be changed" :???:

---

### Post by unicycler on 2006-06-01
can you ln without the sudo?

---

### Post by aleskm on 2006-06-01
yep. but the link doesn't work, when I doubleclick on it, nothing happens. But I'm the owner and group is "root"

---

### Post by unicycler on 2006-06-01
do you have execute permissions?

If you ls -l on your desktop, what does it show?

-rwxr-sr-x

---

### Post by aleskm on 2006-06-01
lrwxrwxrwx 1 ales ales   11 2006-06-01 22:25 commander -> /usr/bin/mc

---

