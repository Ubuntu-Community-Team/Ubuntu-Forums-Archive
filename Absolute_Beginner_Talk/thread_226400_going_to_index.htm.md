---
title: "going to index.htm"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by danilab on 2006-07-31
i'm sure this question must be pretty easy, but im pretty new on apache2.
how do i make apache2 automaticaly go to the index.htm in de directory?
'cause when i go to [http://localhost/](http://localhost/) it shows me the directory and it contains the index.htm file

---

### Post by VirtuAlex on 2006-07-31
try to rename it to index.html

---

### Post by danilab on 2006-07-31
I knew it was pretty simple!

thanks man!

---

### Post by NewbieNik on 2006-07-31
or you could edit the http.conf/apache2.conf in etc/apache/apache2 folders  to use index.htm instead of index.html
just search and replace and it makes this the default.

---

