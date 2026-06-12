---
title: "I bought 120 Gb HD but it says I have only 107"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by narf y akim on 2008-02-03
Hello,
I don't know why the System Manager only detects 107 GB total available space if my laptop has 120. Is there a problem? Should I reinstall Ubuntu?

---

### Post by Majorix on 2008-02-03
I am no hardware wizard but it is a common problem with HDDs.

---

### Post by st33med on 2008-02-03
That is typical of manufactures to do that. When they say 120 GB, they mean 120 *billion* bytes. So, a GB is about 1073741824 bytes, and 120 GB is 128849018880 bytes. Minus that by 120 billon, and you have a difference of 8849018880 bytes (about 8.2 actual GB)

That is normal.

EDIT: Not to mention some more space used by the system.

---

### Post by DMK62 on 2008-02-03
The actual size of your hard drive according to the manufacturer is probably listed as 120 gigabytes and that is based on them using 1 gigabyte = 1000 megabytes. 1 gigabyte is actually 1024 megabytes.

When you add up the space taken up by Ubuntu as well as the fact that Ubuntu reserves a certain % of your drive then 107 sounds well within norm. No need to reinstall.

Dale

---

### Post by narf y akim on 2008-02-03
Ok, thank guys, I feel better now.

---

### Post by kryth on 2008-02-03
Yeah, it's exactly what DMK62.

I though HD makers were sued and were gonna stop that crap. Guess not.

---

