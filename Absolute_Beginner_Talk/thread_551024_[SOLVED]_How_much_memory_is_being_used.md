---
title: "[SOLVED] How much memory is being used ??"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-14
[IMG]http://i8.tinypic.com/2u5z321.jpg[/IMG]

---

### Post by schorsch on 2007-09-14
You are using ~160 MB RAM .... you can trust both figures. The trick is to read the line starting with "-/+ ..." in the output of free.

---

### Post by chrome307 on 2007-09-14
Excellent :)

---

### Post by Majorix on 2007-09-14
The 500mb used that the "free" shows is I believe how much memory is available to the system. Ubuntu for some reason won't "see" the whole ram. Can anybody inform us why?

---

### Post by oilchangeguy on 2007-09-14
> **Majorix said:**
> The 500mb used that the "free" shows is I believe how much memory is available to the system. Ubuntu for some reason won't "see" the whole ram. Can anybody inform us why?

windows does the same thing, if you've got on-board video.

---

### Post by schorsch on 2007-09-14
The listed 500 MB are the whole RAM of the system ..... and you have to consider the amount of RAM that is used by file system caching so it is better to take a look in the line I mentioned .....

---

### Post by rsambuca on 2007-09-14
In the first line the 501940 used includes 329288 cached items.  It is "seeing" everything, and using it as efficiently as it can.

---

### Post by Majorix on 2007-09-14
> **oilchangeguy said:**
> windows does the same thing, if you've got on-board video.

Oh I couldn't think of the onboard video.. Sorry. Thanks for the info.

---

