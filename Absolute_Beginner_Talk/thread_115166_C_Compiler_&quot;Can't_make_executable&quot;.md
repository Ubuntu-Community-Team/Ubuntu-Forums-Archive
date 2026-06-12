---
title: "C Compiler &quot;Can't make executable&quot;"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by CujoQuarrel on 2006-01-10
Whenever I try to do a ./configure on any software package I get a 
"checking for C compiler default output file name... configure: error: C compiler cannot create executables" when it tries to use GCC.

Where do I go to find out the problem?

---

### Post by paulmilliken on 2006-01-10
I'm not sure, however, can you "sudo ./compile"?  If that doesn't work, perhaps you can try another version of gcc (several versions are in the repositories)?

---

### Post by ape on 2006-01-10
Make sure that you have the libc6-dev and build-essential packages installed.

---

### Post by Suger on 2006-01-10
./configure creates a config.log file. If none of the above works, post the content of it here, in between code tags.

---

### Post by brohan on 2006-01-10
It is probably because you don't have the package 'build-essentials' installed, with that in it should run smoothly

---

### Post by daschl on 2006-01-10
also check, that the permissions are set right (700 for example or whatever you like but you need read, write and execution permissions to the dir where ./configure resides)

---

