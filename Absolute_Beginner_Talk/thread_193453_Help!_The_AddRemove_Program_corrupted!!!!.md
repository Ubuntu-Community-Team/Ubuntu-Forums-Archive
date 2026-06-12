---
title: "Help! The Add/Remove Program corrupted!!!!"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2006-06-10
I received this message!

What should I do to check the correctness of the file?

What is that sudo apt-get update command?
Why command not found?

Help!
Thanks!

---

### Post by boom2k1 on 2006-06-10
I mistyped that command before...

I did not change any permission stuff.. 
and I just did the step 2  

and it returned the following

charles@charles-laptop:~$ sudo apt-get update
E: Malformed line 33 in source list /etc/apt/sources.list (dist)


So what should I do? 

Thanks!

---

### Post by adwait on 2006-06-10
There seems to be an error in your sources.list file.....can you post the output of
```
cat /etc/apt/sources.list
```

---

### Post by boom2k1 on 2006-06-10
Thanks anyways!

I have fixed it, and the way to fix it is as following:

charles@charles-laptop:/$ sudo nautilus

then I opened that /etc/apt/sources.list file

and found that line..
it was corresponding to the line
deb [http://cran.R-project.org/bin/linux/debian/stable/](http://cran.R-project.org/bin/linux/debian/stable/)

and the problem is that it should instead be
deb [http://cran.R-project.org/bin/linux/debian](http://cran.R-project.org/bin/linux/debian) stable/
I fixed it and now it ran fine

However, I still don't get why mistyping a path name would screw up the Add/Remove!
(instead of just ignoring the unreadable link!)

---

