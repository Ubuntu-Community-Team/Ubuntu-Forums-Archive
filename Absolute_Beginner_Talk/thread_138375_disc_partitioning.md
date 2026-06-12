---
title: "disc partitioning"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by mzilhao on 2006-03-01
hi,

i've just installed ubuntu. 
i was wondering, should i partition my hard disc? as in, one partition for data files, another for programs, etc... and how can i do that, now that i have my system almost running fine, without messing everything up?

thanks,
Miguel

---

### Post by Xian on 2006-03-01
If you're talking about setting up separate partitions for paths like /etc/, /opt, or /var for example, I would say that it is practically unnecessary and would advise that you not go through the trouble. What reason do you have for asking??

---

### Post by mzilhao on 2006-03-02
well, on windows i have one partition (c: drive) with windows installed and all my programs, and i keep data files (text docs, pdfs etc...) on a separate partition (d: drive). that way, if something happens to the c: drive, i won't loose all my files... 
i was wondering if i should do the same with linux...

---

### Post by Xian on 2006-03-02
There is certainly no harm in keeping a backup partition of important data, but I would suggest reviewing the Linux [filesystem](http://www.debian-administration.org/articles/256) to give you a better understanding of how this setup is different from Windows.

---

### Post by cronholio on 2006-03-02
Some people prefer a different partition for /home (that's where your personal data will be) or even another physical drive but it's not necessary. IMHO the risk of data loss by a corrupted file system is significantly lower when using ReiserFS, if compared to NTFS. Not even speaking of FAT32.

And you should do CD/DVD backups of really important stuff anyway.

---

