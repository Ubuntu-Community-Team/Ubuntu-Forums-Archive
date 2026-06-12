---
title: "How to find text in multiple files?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2007-01-29
I have a website folder that obviously contains a lot of different files. There are a couple of keywords that I would need to locate but have no idea which file it is in. Can someone please tell me the command to find the text without doing a search within each one manually. Thanks.

-Johnny

---

### Post by kidders on 2007-01-29
Hi there,

How about something like **grep "something" *.html** or **find -iname "*.php" -print -exec grep -i "something" {} \;** ? Those will show you extracts from files (with & without descending into subdirs) containing the word "something". Take a look at the man pages for **grep** and **find** for more info.

Hope that helps.

---

### Post by JohnnyAvocado on 2007-01-29
Thanks so much. I was able to find the files I needed.

---

