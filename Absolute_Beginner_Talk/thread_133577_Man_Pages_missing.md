---
title: "Man Pages missing"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by vijayanand_sodadasi on 2006-02-20
I don't know if this is the right forum to ask this question. 
I am trying to search man pages for some information but it seems man pages are not installed on my machine.  For instance I tried to search the following in man pages:

```
vijay@ufonix1:~/prgs$ man execlp
No manual entry for execlp
vijay@ufonix1:~/prgs$ man 2 introduction
No manual entry for introduction in section 2
vijay@ufonix1:~/prgs$ man
What manual page do you want?
vijay@ufonix1:~/prgs$ man 2 read
No manual entry for read in section 2
vijay@ufonix1:~/prgs$ man read
No manual entry for read

```

Where do I find man pages or how do I install them if they are missing?

---

### Post by Klaidas on 2006-02-20
Maybe there just aren't man pages for what you're looking for. Try something like ```
man apt-get
``` Post your output :)

---

### Post by svk on 2008-06-11
A little late, but...

The man pages for sections 2 and 3 are in the manpages-dev package.  Sections 4, 5, and 7 are covered by the manpages package.

This leaves sections 1, 6, and 8.  I'm not really sure where to look for those... My guess is that these sections get filled up whenever you install a new application.  For example, if you install a new game, the documentation for the game will be added to section 6 ("Games") of the manual pages on your system.

---

