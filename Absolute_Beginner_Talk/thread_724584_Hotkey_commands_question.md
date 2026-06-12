---
title: "Hotkey commands question"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Xephyrind on 2008-03-14
alrighty. I am very noobie. Thanks to some posters who encouraged me to ask questions here on the forum. Here I am. Again, Sorry for the nubbiness...

In terminal:

1. what does CTRL-C do? So far it seems like refresh.

2. what does CTRL-Z do?

3. are there any other hotkeys like that?
    a. if yes, where can I read up on them?

4. Is the book Linux in a Nutshell by  Siever, Ellen, Aaron Weber,and Stephen Figgins at right level for me?

5. Does the book go over the very fundamental linux commands and hotkeys like the ones I've asked above?

Thanks for reading this noob-infested message :)

---

### Post by nick_h on 2008-03-14
1. Sends an interrupt signal (SIGINT) to the running process.
2. Stops a job and puts it in the background.
3. Yes. There are CTRL keys to view history (P and N) to clear a line (U) and others.  It depends what you want to do.  Have a look at the manual page for bash.
```
yelp man:bash
```
Look at the Job Control section for details of CTRL-Z.
4&5. I don't have a copy of that book.

---

