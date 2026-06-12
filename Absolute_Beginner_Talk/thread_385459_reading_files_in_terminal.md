---
title: "reading files in terminal"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by strivehosting on 2007-03-15
I am trying to read the 1stRead.txt file in terminal for the scanModem download but I dont know the command to enter.

---

### Post by dbott67 on 2007-03-15
To just display the output:
```
 cat /path/to/file/1stRead.txt
```

To edit in the terminal, you can use vi, vim or nano:
```
 nano /path/to/file/1stRead.txt
```

-Dave

---

### Post by ciscosurfer on 2007-03-15
> **strivehosting said:**
> I am trying to read the 1stRead.txt file in terminal for the scanModem download but I dont know the command to enter.You can use the **cat** command to do this or the **less **or **more **command.  So for example, you can enter in```
cat 1stRead.txt
```and it will appear on screen.  For longer files, using **less** is a good choice and you can page through the file by hitting either the Enter key (line by line) or the Spacebar (to move page by page), so for example```
less 1stRead.txt
```Hope this helps!

---

### Post by strivehosting on 2007-03-15
Thank you guys!!

---

