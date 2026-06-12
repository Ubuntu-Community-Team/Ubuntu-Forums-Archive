---
title: "&quot;-1 Invalid module format&quot; error message but the gcc version are the same"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by nii on 2006-03-15
In my system, gcc-3.4 and gcc 4.0.1.3 coexist.
   
   I re-compiled the kernel last night, so I'm sure the gcc version is gcc-3.4

   And I tried to write a simple kernel module and use gcc-3.4 to compie it.

   But when I  use insmod to install this module. It still give me error message :

   insmod: error inserting 'testmodule.o': -1 Invalid module format

   I have google this error msg.  So if gcc version all the same, any other problem 

   would cause this error!?

   Sorry for my poor English and thanks for any help.

---

### Post by Pragmatist on 2006-03-15
What is the output of:
```
dmesg
```

Also, read this.  Maybe it will help:
[http://www.linuxtopia.org/online_books/Linux_Kernel_Module_Programming_Guide/x181.html](http://www.linuxtopia.org/online_books/Linux_Kernel_Module_Programming_Guide/x181.html)

---

### Post by nii on 2006-03-17
Follow the kernel module guide. It works!!

   Thanks a lot. :)

---

