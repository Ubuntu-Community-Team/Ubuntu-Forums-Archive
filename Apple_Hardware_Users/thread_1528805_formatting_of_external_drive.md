---
title: "formatting of external drive"
date: 2010-07-11
forum: Apple Hardware Users
---

### Post by vsiege on 2010-07-11
Whats the best choice for formatting (file system) an external drive for use between osx and ubuntu? HFS extended?

---

### Post by robsoles on 2010-07-12
I'm gonna bet the absolute majority of formats that OSX can manage can easily be accessed by Ubuntu.

---

### Post by conal on 2010-07-12
I'm wishing I had used HFS+ for this purpose instead of FAT32, because now I can't copy files larger than 4GB to my external hard drive!

---

### Post by robsoles on 2010-07-12
> **conal said:**
> I'm wishing I had used HFS+ for this purpose instead of FAT32, because now I can't copy files larger than 4GB to my external hard drive!

Take all the files from it onto a drive on one of the machines you pair it with and re-format it - if you have an Ubuntu machine then you should have palimpsest ("System"->"Administration"->"Disk Utility") and it is an excellent tool for reformatting.

---

### Post by conal on 2010-07-12
> Take all the files from it onto a drive on one of the machines you pair it with and re-format it - if you have an Ubuntu machine then you should have palimpsest ("System"->"Administration"->"Disk Utility") and it is an excellent tool for reformatting.

Good point but I'm out of room everywhere else. Maybe time to buy an new hard drive? Unless I can somehow resize the FAT32 partition without destroying the data, and create an HFS+ partition for my big files, but that could be risky when I can't back up...

Cheers

Conal

---

