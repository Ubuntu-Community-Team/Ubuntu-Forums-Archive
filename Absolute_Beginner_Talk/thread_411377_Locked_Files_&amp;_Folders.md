---
title: "Locked Files &amp; Folders?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by scottdizzle on 2007-04-16
What does it mean when something has a lock on it and how do I get rid of it? I have directory on my desktop that I don't want anymore but I am not able to delete it. I went to console and logged in with 'su' and tried to rm the directory but I can't remove directories.

so...

1) What is the lock status all about?

2) How do I change, modify, or utilize this lock feature in the future?

3) How can I remove directories with bash commands?

Here's a screenshot so you know what lock I'm talking about:

[img]http://img407.imageshack.us/img407/4922/lockkr1.jpg[/img]

---

### Post by ComplexNumber on 2007-04-16
it means that it can't be written to. try the following:

**sudo rm -R  ~/Desktop/<name-of-directory-here>**

---

### Post by Maestro23 on 2007-04-16
Try:

> sudo rm -R

*man pages give you syntax for terminal commands.  Ex:  man rm (syntax for the remove command)

---

### Post by scottdizzle on 2007-04-16
What is sudo all about? Can I man sudo? I don't remember sudo back in my redhat days.

Oh... su.. do.. like.. super user do this?

---

### Post by NeoLithium on 2007-04-16
Yep; sudo will give you superuser access without logging into root entirely; so it is far safer when you only have a few small commands to run. :)

---

