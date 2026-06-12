---
title: "Home partition used/unused space doesn't add up"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by BackInTimeMan on 2006-10-18
I feel I must be missing something here. My Home partition is 7.26 GB, but if I look at Properties for the Home folder, it says:

Contents: 17191 items, totalling 1.7 GB
Free space: 1.4 GB

Now to me, that gives a total of 3.1 GB. Please, what am I missing? :confused:

---

### Post by po0f on 2006-10-18
BackInTimeMan,

From a terminal run:
```
$ df -h
```

---

### Post by BackInTimeMan on 2006-10-18
> **po0f said:**
> BackInTimeMan,

From a terminal run:
```
$ df -h
```

Right, thanks po0f. The relevent part:

Filesystem    Size    Used    Avail   Use% Mounted on
/dev/hda3     7.2G    5.4G    1.4G    80% /home

Well that looks better, still doesn't quite add up but a lot closer. Do you know why it doesn't show the correct Used value in Properties?

---

### Post by ReaderRat on 2006-10-18
The software counts 1 Meg as 1,000,000 bytes. The HDD vendors count it as 1,024,000 bytes. Don't know why

---

### Post by po0f on 2006-10-18
BackInTimeMan,

It might only be counting the sizes of files in the current directory when you right-click and go to Properties.  This is why I always use the command line for stuff like this.  ;)

---

### Post by Sef on 2006-10-18
> The software counts 1 Meg as 1,000,000 bytes. The HDD vendors count it as 1,024,000 bytes. Don't know why

From t1shopper.com

> But although computer data and file size is normally measured in binary code using the binary number system (counted by factors of two 1, 2, 4, 8, 16, 32, 64, etc), the prefixes for the multiples are based on the metric system!  The nearest binary number to 1,000 is 2^10 or 1,024; thus 1,024 bytes was named a Kilobyte.  So, although a metric "kilo" equals 1,000 (e.g. one kilogram = 1,000 grams), a binary "Kilo" equals 1,024 (e.g. one Kilobyte = 1,024 bytes).  Not surprisingly, this has led to a great deal of confusion.



Go to the [t1shopper]("http://www.t1shopper.com/tools/calculate/") site.

---

### Post by po0f on 2006-10-18
BackInTimeMan,,

It slipped my mind earlier, but you can run this command to get a more accurate listing of what's eating up space in your home directory:
```
$ du -h --max-depth=1 ~
```

---

### Post by BackInTimeMan on 2006-10-19
ReaderRat and Sef,

Thanks, yes, I had forgotten about that. It still doesn't account for the large discrepancy between what is shown in Properties and the $ df -h command though.

---

### Post by BackInTimeMan on 2006-10-19
> **po0f said:**
> BackInTimeMan,,

It slipped my mind earlier, but you can run this command to get a more accurate listing of what's eating up space in your home directory:
```
$ du -h --max-depth=1 ~
```

Thanks poOf, even better! BTW, the size of the files in my Home directory is only 776 MB.

---

