---
title: "Active Directory and winbind"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by dthomasdigital on 2007-04-23
OK, I've gone over the how to's one step at a time, I even tried "sadms", for the love of god please help me. I consider myself at least some what knowledgeable, but man do I feel over whelmed...
I'm very close when I do a wbinfo -u I get a list of the windows users but it will not authenticate on Active Directory.......

Any Ideas?

---

### Post by teamanx on 2007-05-31
The easiest way to join an AD is using SADMS. 

First, you may need to install winbind manually (sudo apt-get winbind).

Second, you should have a look at this post:

[http://ubuntuforums.org/showthread.php?t=45889](http://ubuntuforums.org/showthread.php?t=45889)

Third, install SADMS.


If you want sound support for your AD users, look at his post:

[http://ubuntuforums.org/showthread.php?t=77469&page=2](http://ubuntuforums.org/showthread.php?t=77469&page=2)

Regards.

---

