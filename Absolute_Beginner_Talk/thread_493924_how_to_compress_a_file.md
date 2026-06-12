---
title: "how to compress a file"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-07-06
i want to compress a .doc file in open office .how do i do it?

---

### Post by p_quarles on 2007-07-06
If you can do "in" OpenOffice, I wouldn't know how. The usual way, though, is to use your file manager, right-click on the file, select "make archive" and choose a compressed format (probably either .tar.gz or .zip).

---

### Post by Cypher on 2007-07-06
Compress to what format? ZIP, TAR, GZ, BZ2?

---

### Post by pardesi on 2007-07-06
zip

---

### Post by p_quarles on 2007-07-06
Well, like I said: right-click the file, select "make archive," then choose the .zip format. You can also use the zip command from the CLI.

---

### Post by pardesi on 2007-07-06
thanks taht worked

---

### Post by kyousukun on 2007-07-13
how do i choose the compression ratio? (i.e. -1 fastest, -9 best)?
i want to compress an image album of 4mb+ into sumthing around less than 1MB or something.

---

### Post by p_quarles on 2007-07-13
> **kyousukun said:**
> how do i choose the compression ratio? (i.e. -1 fastest, -9 best)?
i want to compress an image album of 4mb+ into sumthing around less than 1MB or something.
4 MB to 1 MB is not likely to happen with pictures. You'll be lucky to get, say, 2.6 MB.

Here's how you do it, though: cd into the directory above the one you want to compress. Then, enter```
zip -9 pictures.zip directory/
```
In the above, replace "directory" with the actual name of the directory you want to archive.

---

### Post by kyousukun on 2007-07-15
> **p_quarles said:**
> 4 MB to 1 MB is not likely to happen with pictures. You'll be lucky to get, say, 2.6 MB.

Here's how you do it, though: cd into the directory above the one you want to compress. Then, enter```
zip -9 pictures.zip directory/
```
In the above, replace "directory" with the actual name of the directory you want to archive.

thanks p_quarles, when i ZIPed the folder containing the pictures from 5mb, it compressed to 138KB
this is really nice thanks for this.
unfortunately what was zipped was the folder, not the contents of the folder.

---

