---
title: "&quot;error while loading shared libraries: libwx_gtk-2.2.so&quot;:no such file.// what to do ?"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-01-14
"error while loading shared libraries: libwx_gtk-2.2.so":no such file.// what to do ?
============================  
  
What to apt-get ? what to install ?

 Someone has an idea ?? 
  
Thank you very much §!
Patrick

---

### Post by Perfect Storm on 2006-01-14
try with apt-get libwxgtk2.4-dev (if you are trying to compile something)


if it still does ask for it you may have to make a symblink.

---

### Post by patrick295767 on 2006-01-14
I always knew you were very good with Linux Box !! 
Then, you became Ubuntu forum staff : Big Congratulations AI!!  
  
And of course, your help worked very well !!
  ```
apt-get -f install libwxgtk2.4-dev 
```  
worked !! 
  
I'll let you know about my progress with my compiling stuffs ... 
  
Thanks again, 

Greetz

Pat

---

