---
title: "[SOLVED] How do I find my localhost?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by curiousnoob on 2007-09-23
I am sure this is a REALLY dumb question, but how do I find my hostname.  
I am trying to do what is recommended here:
[http://ubuntuforums.org/showthread.php?t=388765](http://ubuntuforums.org/showthread.php?t=388765)

When I try the intructions I get this output which is different from other peoples examples. 

127.0.0.1	localhost
127.0.1.1	johnsmith-desktop

---

### Post by overdrank on 2007-09-23
> **curiousnoob said:**
> I am sure this is a REALLY dumb question, but how do I find my hostname.  
I am trying to do what is recommended here:
[http://ubuntuforums.org/showthread.php?t=388765](http://ubuntuforums.org/showthread.php?t=388765)

When I try the intructions I get this output which is different from other peoples examples. 

127.0.0.1	localhost
127.0.1.1	johnsmith-desktop

HI
example

My current /etc/hosts shows up as:
Quote:
127.0.0.1 localhost
127.0.1.1 LTvH.SPHOR
Changed to:
Quote:
127.0.0.1 localhost LTvH.SPHOR
127.0.1.1 LTvH.SPHOR
yours 
127.0.0.1	localhost
127.0.1.1	johnsmith-desktop
Change to 
127.0.0.1	localhost johnsmith-desktop
127.0.1.1	johnsmith-desktop

As i understand it
:popcorn:

---

### Post by pingpongboss on 2007-09-23
in simpler terms, your host name is ```
johnsmith-desktop
```

---

