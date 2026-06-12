---
title: "gzip problem"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by aum11 on 2005-11-15
I have downloaded a tar.gz file.

When I double click on the fiel, the archive manager starts and then says archive type is not recognised.

If I try to use the "open the file with another application", it does not offer gzip as an option.

Gzip is installed under Breezy, according to Synaptic.


What to do?  I am sure there is a very simple answer to such a basic operation.....

Thanks.

---

### Post by matthewv on 2005-11-15
try (in terminal) gunzip <file.tar.gz>

---

### Post by aum11 on 2005-11-15
Thanks Mathew.

I just realised that the downloaded gz file had been given a name with quotes front and back.  When I removed them, it all unzipped fine.

A trap for young players!!

---

