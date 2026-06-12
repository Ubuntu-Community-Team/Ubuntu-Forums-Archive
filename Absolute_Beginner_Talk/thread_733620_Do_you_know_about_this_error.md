---
title: "Do you know about this error?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Anjue on 2008-03-24
when I use command "sudo dpkg-reconfigure -a" I got this error 

> /var/lib/scrollkeeper/nl/scrollkeeper_cl.xml:1: parser error : Document is empty

^
/var/lib/scrollkeeper/nl/scrollkeeper_cl.xml:1: parser error : Start tag expected, '<' not found


what is it? and How to fix it?

thank you for any reply

---

### Post by Ocxic on 2008-03-24
It means that there is something wrong with that file, it should have something in it that is different from the actual contents.

I do not know how to fix this though. maybe try "sudo apt-get install --reinstall scrollkeeper"

---

