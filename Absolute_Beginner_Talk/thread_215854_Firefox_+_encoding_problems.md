---
title: "Firefox + encoding problems"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2006-07-14
Hello there! Dunno if this is the right place to ask, but since you guys know everything. I'm giving a try:

Ok, I have eclipse (using ISO-8859-1 encoding for files). So I'm coding my jsp using special characters for portuguese language (like ç). Well, they're displayed inside eclipse, but on firefox I get an interrogation mark (&#65533;) instead. 
Most of my CVS files that comes from users using windows, also get this. And sometimes some of the javadocs on classes that also came from windows machine get messed up. 

What's the correct encoding I should be using?

Regards

---

### Post by tenshi-no-shi on 2006-07-20
I had the same problem till I found the solution on the firefox message boards, go to view->character encoding->autodetect and select universal. I got ride of it for me, as far as I can see.

---

