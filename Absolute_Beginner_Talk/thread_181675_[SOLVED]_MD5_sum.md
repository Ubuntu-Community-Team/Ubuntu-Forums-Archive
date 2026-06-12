---
title: "[SOLVED] MD5 sum"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-05-24
I have a Linux LN3 installed and I wonder if there is a MD5 Sum Generator available for Linux? I only know the MD5Summer for Windows. For example, do I have to go back to Windows in order to generate or check a MD5 Sum of an iso file?
:confused:

---

### Post by tkjacobsen on 2006-05-24
the command md5sum will do it all:
```
md5sum FILE
```

this will output the md5sum of FILE

if you have a file (.md5) containing md5sums for FILE:
```
md5sum -c FILE.md5
```
then the output will be "ok" if the md5sum is correct

---

### Post by byen on 2006-05-24
Yes! 
```
md5sum filename 
```
in the terminal should work perfectly! Usually Most linux distributions have this utility built-in in the OS and should work without the need for any configuration.

---

### Post by Cariboo1938 on 2008-02-19
Thank you for the response...Case closed!

---

