---
title: "MD5 Checksum program in Ubuntu?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-10-14
I was wondering if there was an Md5 checksum program in Ubuntu that would allow you to compare MD5 checksums of individual files

thanks

---

### Post by Pumalite on 2007-10-14
[http://www.delorie.com/gnu/docs/textutils/md5sum.1.html](http://www.delorie.com/gnu/docs/textutils/md5sum.1.html)
[http://linux.about.com/library/cmd/blcmdl1_md5sum.htm](http://linux.about.com/library/cmd/blcmdl1_md5sum.htm)
k3b does an md5sum on iso automatically before burn.

---

### Post by julian67 on 2007-10-14
> **JasonBourneLinux said:**
> I was wondering if there was an Md5 checksum program in Ubuntu that would allow you to compare MD5 checksums of individual files

thanks

It's built in by default. To get the md5sum of a file open a terminal and ```
md5sum yourfile
```

To verify files from a list of md5sums:

```
md5sum -c yourlistofchecksums
```

The list and the files should be in the same folder.

To learn more:

```
man md5sum
```

GNU/Linux and other free OS are full of these essential utilities, you don't have to waste your time with freeware and shareware and paid  proprietary applications just to perform normal tasks.

---

