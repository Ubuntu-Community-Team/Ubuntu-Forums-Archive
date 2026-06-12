---
title: "I am not able to browse files Says: No Directory found"
date: 2014-08-02
forum: Any Other OS
---

### Post by AbhimanyuAryan on 2014-08-02
I am using Kali linux before that i was using linux mint cinammon & was facing the same problem. I have this strange problem. I am able to access few files but not all. In some cases it doesn't browse for my files. 

I have installed Kali on my one TB partitioned hard drive. Everything seems to work fine except this no directory found problem. Please have a look at the attachment.

---

### Post by ajonen on 2014-08-03
please display the permissions with ls -al

also display the folder permissions and report back.

---

### Post by oldos2er on 2014-08-03
Moved to Other Operating Systems and Projects.

---

### Post by AbhimanyuAryan on 2014-08-04
root@HackerInside:~# cd C
root@HackerInside:~/C# ls -al
total 64
drwxr-xr-x  2 root root 4096 Aug  3 06:05 .
drwxr-xr-x 34 root root 4096 Aug  5 04:18 ..
-rwxr-xr-x  1 root root 6887 Jul 26 15:56 a.out
-rw-r--r--  1 root root  305 Aug  3 05:16 dir.c
-rw-r--r--  1 root root  619 Aug  3 05:07 dirent.h 
-rwxr-xr-x  1 root root 6887 Aug  3 06:03 err
-rw-r--r--  1 root root  130 Jul 26 15:46 error.c
-rw-r--r--  1 root root  137 Jul 26 15:55 fix.c 
-rw-r--r--  1 root root   92 Jul 26 15:40 getchar.c 
-rw-r--r--  1 root root   73 Jul 26 15:36 hello.c
-rwxr-xr-x  1 root root 6775 Jul 26 15:37 hi
-rw-r--r--  1 root root  306 Aug  3 05:21 nano.save
-rw-------  1 root root    1 Aug  3 06:05 nano.save.1
root@HackerInside:~/C#

---

