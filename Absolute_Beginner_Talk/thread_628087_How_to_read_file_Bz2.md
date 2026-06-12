---
title: "How to read file Bz2"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by My_Ausweis on 2007-11-30
Dear All

Anyone know how to read file with ext bz2 ?

Thx

L.M

---

### Post by dhobbs on 2007-11-30
bz2 is a compression used on files, similar to zip.  You can use the 'tar' program to extract the archive.  You need to use the -j option to decompress the file.

Or an easier way to use a GUI decompression program.  Have you tried to double-click the file to open it?

---

### Post by dhobbs on 2007-11-30
```
tar -jxvf <filename>
```
That's the command you would run in the terminal on a file if it's a .tar.bz2 file

```
bunzip2 <filename>
```
If it's just .bz2

---

