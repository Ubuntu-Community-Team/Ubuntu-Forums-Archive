---
title: "[SOLVED] apt get-install"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-09-01
Does downloading programs (that aren't in the repositories) using the apt-get command cause any damage or hurt the performance of the Ubuntu OS?
Example: Scribus. 
Thanks for the help of everyone on this forum. I have learned a lot just looking through the questions asked and the answers. Ubuntu rocks:guitar:

---

### Post by por100pre1 on 2007-09-01
Scribus is in the repos... Which version of Ubuntu are you using?

---

### Post by forestpixie on 2007-09-01
no - it's the way to go - if you can apt-get install it's in your source.list repos

Once you get used to using it - it's easier than add/remove and synaptic

you can use it to search as well if you've some idea of the name

sudo apt-cache search whatyoulookfor

---

### Post by por100pre1 on 2007-09-01
> **forestpixie said:**
> no - it's the way to go - if you can apt-get install it's in your source.list repos

Once you get used to using it - it's easier than add/remove and synaptic

you can use it to search as well if you've some idea of the name

sudo apt-cache search whatyoulookfor

Another way to check is:

```
aptitude search whatyouwanttofind
```

---

### Post by forestpixie on 2007-09-01
he he - love these forums - didn't know that one :)

---

### Post by por100pre1 on 2007-09-01
> **forestpixie said:**
> he he - love these forums - didn't know that one :)

This one is even cooler, to download a package without installing:

```
aptitude download whatyouneed
```

useful for saving packages... :)

---

