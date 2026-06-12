---
title: "Restoring Ubuntu's state?"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by gt24 on 2006-03-27
One issue with Ubuntu is that I feel completely out of control in relation to the file system.  A huge issue in relation to this is libraries...

I call program A that depends on B C D E F.  Later on, I uninstall program A, I don't exactly like it.  The pieces B C D E F stay, clogging up my system.  Unless I specifically know why they were added and that they would be safe to delete, they stay on my hard drive and "clog up" Ubuntu.

Here is my two part question.  First off, how do I manage this problem?  My key question is a proposed solution to that first question, if it works.  My second question... could I feed apt-get a list of packages that I want (meaning, the NORMAL Ubuntu distro packages only) and have apt-get dynamically uninstall any packages not on that white list?  If I could do that then I could refresh my Ubuntu install to a factory fresh state minus the whole reinstall bit.  If not, well... I wonder what a possible solution is...

---

### Post by aysiu on 2006-03-27
I believe that doing an *aptitude* install instead of an *apt-get* install lets you remove packages that got installed *with* a particular package.

You can also try using *deborphan*.

---

