---
title: "ddd debugger"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by rob21 on 2008-02-09
when in the ddd debugger with my project compiled properly and source files loaded onto the GDB console source window, when I try to set a breakpoint I get the message "no line 9 in file driver.c", or "no line 10 in file driver.c". The debugger seems to be acknowledging only one or two of the lines in my driver. Please help.
              thanks

---

### Post by happysmileman on 2008-02-09
Have you compiled it with debug info... If you're using an IDE like KDevelop, you should be able to choose between "debug", "default" and "optimised" or something, and AFAIK only the debug profile will work like this.

I'm not sure how to compile it like that without the IDE though, it's been a long time since I've done it myself :p

---

