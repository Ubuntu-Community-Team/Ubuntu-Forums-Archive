---
title: "bin file not executing"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by atsugi on 2007-10-21
don't know if this belongs in the beginner forum or not. I have been trying to execute a bin file in the terminal and am having issues. I am running the latest x64 stable.

first I set the permissions
chmod a+x file.bin

then when I try the next step I have issues

./file.bin


it gives me:

ELF file or directory not found

I don't know what I am doing wrong, please help

Atsugi

---

### Post by HermanAB on 2007-10-21
First do 'ls -al' to see who the file belongs to and what the permissions are.  If the file belongs to root, then a common user can change it, unless you use sudo.

Cheers,

H.

---

### Post by atsugi on 2007-10-21
i have done that as well..the permissions are right but still no luck

---

