---
title: "ldconfig"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-06-12
When ever i want to run a certain program i have to type this:

sudo ldconfig /usr/lib/firefox

before it will work. Is there a way of permenently settng it up?

What does it actually do anyway? Im guessing its pointing to firefox to borrow its browser elements.

---

### Post by Cypher on 2007-06-12
Add the path "/usr/lib/firefox" to the file "/etc/ld.so.conf" and execute "sudo ldconfig" once. You shouldnt' have to do it again after that..

---

