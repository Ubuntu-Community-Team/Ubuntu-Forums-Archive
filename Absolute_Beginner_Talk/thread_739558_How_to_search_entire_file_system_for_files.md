---
title: "How to search entire file system for files"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by bluewhale on 2008-03-29
I'm fairly new to Ubuntu/Linux. Perhaps it's obvious. but my Google/Search skills are coming up blank here. 

I would like to find the 4 files that are each VMWare client under Ubuntu 7.10 64 bit. I haven't been able to find a GUI or CLI way to search the same way ( sorry ) that Windows does. Setting for a specific file suffix, searching all directories including admin/root, listing hidden files, and most importantly searching all sub directories. 

Might someone kindly direct me toward the FAQ I missed? ](*,)

---

### Post by nsche on 2008-03-29
I guess I am old school but I am not aware of how to search with some gui.  Just bring up a terminal and type find [place to start] -name [filename]   You can use wild cards in the filename if escaped like find /usr -name \*lib   You might want to do it with a sudo if you need to search root or someplace which will generate a lot of errors because of access rights.  There are a lot of options for find.  You can search by access or modified date or most any other file characteristic and then do something like process it through some filter or even string a bunch of options together.  Beware of case in the filenames though if you come from the MS side.

---

### Post by bswilson on 2008-03-29
> **bluewhale said:**
> I would like to find the 4 files that are each VMWare client under Ubuntu 7.10 64 bit.

Try this command using the **find** program.

```
$ sudo find / -name *.vmdk |grep vmdk |more
```

> **bluewhale said:**
> Might someone kindly direct me toward the FAQ I missed? ](*,)

The find program is an excellent one.  Even better than the man page is [this excellent tutorial]("http://dmiessler.com/study/find/") on using **find** and **xargs**.

---

