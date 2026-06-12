---
title: "man pages"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Mikhail on 2006-07-05
Forgive me if this question is asked frequently, but I tried at the terminal "man atoi", and many other C functions and found that I don't have the appropriate man pages for the C library.  I tried installing the glibc-doc package but that didn't do.  Anyone know what to do?  Thank you

---

### Post by MaximB on 2006-07-05
yes you are right - there are some commands that do not have "man" pages
instad you can use the "info" command to get more help
but there are a few commands that do not have "info" like your "atoi" command.

---

### Post by Mikhail on 2006-07-05
So is there nothing I can do about it?

---

### Post by MaximB on 2006-07-05
what is the "atoi" command ?
and what do you want to do ?

---

### Post by T700 on 2006-07-05
Interestingly, you can go to Google and put in "man atoi" (no quotes) and get quite a [wealth of answers]("http://www.google.com/search?num=50&hs=uhD&hl=en&lr=&newwindow=1&safe=off&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=man+atoi&btnG=Search").  It must exist in *some* distros man pages.

Paul

---

### Post by vali on 2006-07-05
Try installing manpages-dev

---

### Post by Mikhail on 2006-07-05
That did it.  Thanks very much.

---

