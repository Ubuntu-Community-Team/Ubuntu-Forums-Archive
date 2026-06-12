---
title: "[SOLVED] What is /var /usr and /temp used for"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-04-15
What are the /var, /usr, /temp and /boot partitions mainly used for? I read in many posts that it is a good idea to have the above partitions. I know that / is the root , /home will be used to place the documents and the settings (of the user?) and of course we can have other partitions where we can place our data. But the posts dont explain what kind of information is stored in these partitions.
 
Any help would be nice !

---

### Post by Maestro23 on 2007-04-15
A guided tour:[http://linuxcommand.org/lts0040.php](http://linuxcommand.org/lts0040.php)

---

### Post by Inxsible on 2007-04-15
> **Maestro23 said:**
> A guided tour:[http://linuxcommand.org/lts0040.php](http://linuxcommand.org/lts0040.php)
 
Thanks ..that helped a lot. Will all the partitions listed there be created during the install automatically or will I have to create each one of those that I want/need?

---

### Post by seshomaru samma on 2007-04-15
it you use the automatic option it will just create / and swap
if you choose manual you can do whatever you want
i usually just make 3 partitions:
/
/home
swap

---

