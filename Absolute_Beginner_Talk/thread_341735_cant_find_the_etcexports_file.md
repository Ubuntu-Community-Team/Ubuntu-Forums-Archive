---
title: "cant find the /etc/exports file??"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-01-19
At the moment I'm reading a few books trying to learn about NFS and in Linux there is supposed to be a file /etc/exports that lets you configure your server. But I cannot find it??

---

### Post by Sir_Yaro on 2007-01-19
create it

---

### Post by nite owl on 2007-01-19
Is that what you'd usually have to do.. Or is it usually already in there?

---

### Post by Sir_Yaro on 2007-01-19
it's depend. But I'd say that files usualy already exist.

---

### Post by bodhi.zazen on 2007-01-19
It should already be there.

If you do not open the file as root it will be blank.

Example:

nano /etc/exports = blank 

sudo nano /etc/exports = file contens

But if there is no file you will get an error message, "file not found" ....

---

