---
title: "C++ compiler?"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by OMRebel on 2006-05-14
I'm taking a C++ course this quarter, and need to know what is a good C++ compiler that I can install on Ubuntu?  I dual boot on my desktop, but only have Ubuntu on my notebook, and I carry that with me whenever I go out of town on the weekends.  Any suggestions?

---

### Post by cgjones on 2006-05-14
If you install the build-essential packages, you'll have both the gcc and g++ compilers.

---

### Post by catlett on 2006-05-14
In case you're new, you get that program by going into the terminal and entering```
 sudo apt-get install build-essential
```

---

### Post by OMRebel on 2006-05-14
Thanks for the responses.  I found Anjuta, and it's working perfectly for what I'm needing.  Thanks again for the responses though.

---

### Post by harisund on 2006-05-14
You might already know this, but Anjuta is an IDE (integrated developer environment) that gives you fancy eye candy that helps with the writing of code. 

However, it too uses gcc/g++ for the underlying compiler.

---

