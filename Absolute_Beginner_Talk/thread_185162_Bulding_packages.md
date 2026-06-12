---
title: "Bulding packages"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by kart3r on 2006-05-31
I'm doing some school work about linux and I need to explain how to add options to a package like this: I want to install php5 with oci support. How do I do that?Or if possible indicate me some tutorial to do this kind of work.

---

### Post by Dr. Nick on 2006-05-31
Hmm.. This is how I think it works, could be wrong though.

If the package is made to use a certain thing, but doesnt necessarily require it to function it will enable it for you most of the times if you have it installed ,along with the corresponding -dev packages for it. If it is a beta feature that isnt enabled automatically then try 

./configure --enable-xxxx

---

